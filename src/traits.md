# Traits

Rust lets you abstract over types with traits. They're similar to interfaces:

```rust,editable
struct Dog { name: String }
struct Cat; // No name needed, cats won't respond to it anyway.

trait Pet {
    fn talk(&self) -> String;
}

impl Pet for Dog {
    fn talk(&self) -> String { format!("Woof, my name is {}!", self.name) }
}

impl Pet for Cat {
    fn talk(&self) -> String { String::from("Miau!") }
}

fn greet<P: Pet>(pet: &P) {
    println!("Oh you're a cutie! What's your name? {}", pet.talk());
}

fn main() {
    let fido = Dog { name: String::from("Fido") };
    greet(&fido);

    let captain_floof = Cat;
    greet(&captain_floof);
}
```
