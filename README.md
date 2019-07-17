# MyTypefaceSpan

Using custom fonts with Spanned strings is a real pain.  This class greatly reduces that pain.

Just add this class to your project and go.  There are detailed javadocs in the class itself, 
but just in case you're too busy to get to it, here's the scoop:

<strong>USAGE</strong><br>
* Get your custom Typeface any way you like.  (I prefer using
the FontCache class as it avoids memory leaks.)
* Get a SpannableStringBuilder setup with the proper string
put in.
* Instantiate this class with your Typeface.
* Set the span in your SpannableStringBuilder, using <em>this class instance</em>
instead of a Typeface instance.  That's the key trick!
* Use this anywhere you like--the font will have been changed for the
designated span.

<strong>example</strong><br>
```java
// Changes the font of the word 'favorite' to a fancy one for a TextView

Typeface tf = FontCache.get("fonts/my_fancy_font.ttf", getApplicationContext());

MyTypefaceSpan myTypefaceSpan = new MyTypefaceSpan(tf);

SpannableStringBuilder sb = new SpannableStringBuilder("my favorite bug");

sb.setSpan(myTypefaceSpan, 3, 10, Spanned.SPAN_EXCLUSIVE_EXCLUSIVE);

myTextView.setText(sb);
```

NOTE: Some fonts just don't work with Android. Hard to tell which
are which without trying a few of 'em. But if Android likes 'em,
this class will show 'em.
