# Splash Activity Demo

splashactivitydemo-melvincabatuan created by Classroom for GitHub

This assignment presents a simple Splash screen implementation.


## Problem:

Design and implement an Android app Splash screen activity with animation.


## Accept

To accept the assignment, click the following URL:

https://classroom.github.com/assignment-invitations/d8aab198953cb4c32134dc3682a8ade9

## Sample Solution:

https://github.com/DeLaSalleUniversity-Manila/splashactivitydemo-melvincabatuan

## Keypoints:

Including 'fade' animation in the SplashActivity.java
```Java
  /**
     * Helper method to start the animation on the splash screen
     */
    private void startAnimating() {
        // Fade in top title
        TextView logo1 = (TextView) findViewById(R.id.TextViewTopTitle);
        Animation fade1 = AnimationUtils.loadAnimation(this, R.anim.fade_in);
        logo1.startAnimation(fade1);
        // Fade in bottom title after a built-in delay.
        TextView logo2 = (TextView) findViewById(R.id.TextViewBottomTitle);
        Animation fade2 = AnimationUtils.loadAnimation(this, R.anim.fade_in2);
        logo2.startAnimation(fade2);
        // Transition to Main Menu when bottom title finishes animating
        fade2.setAnimationListener(new Animation.AnimationListener() {
            @Override
            public void onAnimationEnd(Animation animation) {
                // The animation has ended, transition to the Main Menu screen
               Intent i = new Intent(SplashActivity.this,
                        MainActivity.class);
                startActivity(i);
                SplashActivity.this.finish();
            }

            @Override
            public void onAnimationRepeat(Animation animation) {
            }

            @Override
            public void onAnimationStart(Animation animation) {
            }


        });
        // Load animations for all views within the TableLayout
        Animation spinin = AnimationUtils.loadAnimation(this,
                R.anim.custom_anim);
        LayoutAnimationController controller = new LayoutAnimationController(
                spinin);
        TableLayout table = (TableLayout) findViewById(R.id.TableLayout01);
        for (int i = 0; i < table.getChildCount(); i++) {
            TableRow row = (TableRow) table.getChildAt(i);
            row.setLayoutAnimation(controller);
        }
    }
```

In fade_in.xml:
```xml
<?xml version="1.0" encoding="utf-8" ?>
<set
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:shareInterpolator="false">
    <alpha
        android:fromAlpha="0.0"
        android:toAlpha="1.0"
        android:duration="2500">
    </alpha>
</set>
```

In fade_in2.xml:
```xml
<?xml version="1.0" encoding="utf-8" ?>
<set
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:shareInterpolator="false">
    <alpha
        android:fromAlpha="0.0"
        android:toAlpha="1.0"
        android:duration="2500"
        android:startOffset="2500">
    </alpha>
</set>
```

In custom_anim.xml
```xml
<?xml version="1.0" encoding="utf-8" ?>
<set
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:shareInterpolator="false">
    <rotate
        android:fromDegrees="0"
        android:toDegrees="360"
        android:pivotX="50%"
        android:pivotY="50%"
        android:duration="2000" />
    <alpha
        android:fromAlpha="0.0"
        android:toAlpha="1.0"
        android:duration="2000">
    </alpha>
    <scale
        android:pivotX="50%"
        android:pivotY="50%"
        android:fromXScale=".1"
        android:fromYScale=".1"
        android:toXScale="1.0"
        android:toYScale="1.0"
        android:duration="2000" />
</set>
```


## Submission Procedure with Git: 

```shell
$ cd /path/to/your/android/app/
$ git init
$ git add –all
$ git commit -m "your message, e.x. Assignment 1 submission"
$ git remote add origin <Assignment link copied from assignment github, e.x. https://github.com/DeLaSalleUniversity-Manila/secondactivityassignment-melvincabatuan.git>
$ git push -u origin master
<then Enter Username and Password>
```

Sample:

https://gist.github.com/melvincabatuan/b788b1d69e16fcca81e1 


## Screenshots:

![alt tag](https://github.com/DeLaSalleUniversity-Manila/splashactivitydemo-melvincabatuan/blob/master/device-2015-10-05-214850.png)

![alt tag](https://github.com/DeLaSalleUniversity-Manila/splashactivitydemo-melvincabatuan/blob/master/device-2015-10-05-214922.png)

![alt tag](https://github.com/DeLaSalleUniversity-Manila/splashactivitydemo-melvincabatuan/blob/master/device-2015-10-05-214937.png)

"*Chance is a word devoid of sense, nothing can exist without a cause.*" - Voltaire
