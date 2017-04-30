# CountView
仿支付宝的数字增长效果

代码很简单：
```
 class CountView extends android.support.v7.widget.AppCompatTextView {
    //动画时长 ms
    int duration = 1500;
    float number;
    public CountView(Context context, AttributeSet attrs) {
        super(context, attrs);
    }
    public void showNumberWithAnimation(float number) {
        //修改number属性，会调用setNumber方法
        ObjectAnimator objectAnimator=ObjectAnimator.ofFloat(this,"number",0,number);
        objectAnimator.setDuration(duration);
        //加速器，从慢到快到再到慢
        objectAnimator.setInterpolator(new AccelerateDecelerateInterpolator());
        objectAnimator.start();
    }
    public float getNumber() {
        return number;
    }
    public void setNumber(float number) {
        this.number = number;
        setText(String.format("%1$07.2f",number));
    }
}
```

使用：
```
CountView countView = (CountView) findViewById(R.id.coountview); 
countView.showNumberWithAnimation(100000);
```
