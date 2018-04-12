# TestMockAlipay
高仿支付宝支付密码
# ImitateAlipayPasswordInput
参考支付宝密码输入对话框设计，已经封装成Android Library，导入即可使用。
##效果图
![密码输入框效果图](http://upload-images.jianshu.io/upload_images/1743063-a16c1bf59caf5d41.gif?imageMogr2/auto-orient/strip)
#欢迎大家在此基础上再次完善功能，提高用户体验。
~~~
  mKeypad = new PasswordKeypad();
        mKeypad.setPasswordCount(6);
        mKeypad.setShowinputPassword(false);
        mKeypad.setCallback(new Callback() {
            @Override
            public void onForgetPassword() {
                Toast.makeText(getApplicationContext(),"忘记密码",Toast.LENGTH_LONG).show();
            }

            @Override
            public void onInputCompleted(CharSequence password,boolean Verification) {
                Toast.makeText(getApplicationContext(),"完成密码输入："+password.toString(),Toast.LENGTH_LONG).show();
              /*  mKeypad.dismiss();*/
               new Handler().postDelayed(new Runnable() {
                    @Override
                    public void run() {
                        if (state) {
                            mKeypad.setPasswordState(true);
                            state = false;
                        } else {
                            mKeypad.setPasswordState(false, "密码输入错误");
                            state = true;
                        }
                    }
                },1000);
            }

            @Override
            public void onPasswordCorrectly() {
                mKeypad.dismiss();
            }

            @Override
            public void onCancel() {
                //todo:做一些埋点类的需求
            }

            @Override
            public void goSettingPassWord() {
               Toast.makeText(MainActivity.this,"去设置密码",Toast.LENGTH_LONG).show();
            }
        });
        findViewById(R.id.button).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                mKeypad.show(getSupportFragmentManager(), "PasswordKeypad");
            }
~~~
