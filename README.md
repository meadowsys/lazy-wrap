# lazy-wrap

**NOTE:** Please use version v0.4.1 or above, as versions below it likely have too relaxed `Send` and `Sync` requirements, which can lead to soundness issues.

Smol wrapper around a type with an attached initialisation function. On first access, it'll call the attached function to initialise the value. Implements `Deref` and `DerefMut`.

You can create this in a `static` variable. This would look something like:

```rs
static STATIC_STRING: LazyWrap<String> = LazyWrap::new(|| {
   // do whatever
   "hallo!!!".into()
});
```

I've done my best, but its not tested for soundness when used in multithreaded situations (singlethread is perfectly okay), so use at your own risk. Please do file issues if you find any however, it would be very much appreciated c:
