# dyn Trait

The `dyn Trait` feature is a new way of writing trait objects. In short:

* `Box<Trait>` becomes `Box<dyn Trait>`
* `&Trait` and `&mut Trait` become `&dyn Trait` and `&mut dyn Trait`

And so on. In code:

```rust
trait Trait {}

impl Trait for i32 {}

// old
fn function1() -> Box<Trait> {
# unimplemented!()
}

// new
fn function2() -> Box<dyn Trait> {
# unimplemented!()
}
```

That's it!

## More details

Using just the trait name for trait objects has turned out to be a bad
decision. The current syntax is often ambiguous and confusing, even to
veterans, and favors a feature that is not more frequently used than its
alternatives, is sometimes slower, and often cannot be used at all when its
alternatives can.

Furthermore, with `impl Trait` arriving, "`impl Trait` vs `dyn Trait`" is much
more symmetric, and therefore a bit nicer, than "`impl Trait` vs `Trait`".