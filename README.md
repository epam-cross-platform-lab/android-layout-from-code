# Android Layout From Code

[![PDD status](https://www.0pdd.com/svg?name=epam-cross-platform-lab/android-layout-from-code)](https://www.0pdd.com/p?name=epam-cross-platform-lab/android-layout-from-code)


This project dedicates to help to create layout from code in Android.
Because it is better, than axml.
This library is just a wrapper around native functionality. A way to mimic all functionality from axml, but without axml.

## Why?

1. Code is clearer.
2. Code has type validation.
3. Code has IntellySense.
4. Code has if/for statements.
5. Code has extension methods.
6. Code is faster, do not require reflection.
7. Code is better for scaling, better for reuse.
8. Code layout is simplier to maintain, no need to look into two files at the same time.
9. No FindViewById<T> anymore.
10. Do not require aapt.exe to run, 5 times faster build time.

## Getting Started

Here is a code sample of layout from code using ConstraintLayout.

``` cs
public override View OnCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState)
{
	var view = new ConstraintLayout(Context);

	var myCaseLog = new AppCompatButton(Context);
	myCaseLog.Text = "My Case Log";
	myCaseLog.AddInto(view, x => x
		.WidthOfParent()
		.Height(40.Dp())
		.MarginHorizontal(16.Dp())
		.BottomToBottomOfParent(8.Dp()));

	var postCase = new AppCompatButton(Context);
	postCase.Text = "PostCase";
	postCase.AddInto(view, x => x
		.WidthOfParent()
		.Height(41.Dp())
		.MarginHorizontal(16.Dp())
		.BottomToTopOf(myCaseLog, 8.Dp()));

	list = new RecyclerView(Context);
	list.SetLayoutManager(new LinearLayoutManager(Context));
	list.VerticalScrollBarEnabled = true;
	list.AddInto(view, x => x
		.WidthOfParent()
		.TopToTopOfParent()
		.BottomToTopOf(postCase, 8.Dp()));

	return view;
}
```

## Key Concepts

### Dp and Px

### LayoutParameters

### Extension methods

# Disclaimer

AndroidLayoutFromCode is a **proof of concept**. There is **no** official support. Use at your own risk.
