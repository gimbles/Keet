# Parakeet
✨ A minimal, tiny and easy to use build system for Unix-like OSs made with <3 and Ruby!

# Lovely! How do I add it to my project?
Using parakeet is really simple, you just clone the file and chuck it in your projects root folder, it's design is minimal and straight to the point. You simply add your profiles and commands to the script and.. congrats! You have now successfully added parakeet to your project :)      
      
Here's a handy command to install it in your project! - `wget https://git.io/InstallParakeet` 

# But, How do I configure it?
Configuring parakeet doesn't require any knowledge of the Ruby language, even though it may seem like it at first. Here's an example!

```ruby
GREET = "Welcome to the Zen build system"
PROFILES = ["Debug", "Performance", "Production", "Format", "Clean"]
COMMANDS = {
  "debug" => {
    "Darwin" => ["cargo build"],
    "Linux" => ["cargo build"],
  },
  "performance" => {
    "Darwin" => ["cargo build --release"],
    "Linux" => ["cargo build --release"],
  },
  "production" => {
    "Darwin" => ["cargo +nightly build -Z build-std=std,panic_abort -Z build-std-features=panic_immediate_abort --target aarch64-apple-darwin --release"],
    "Linux" => ["cargo +nightly build -Z build-std=std,panic_abort -Z build-std-features=panic_immediate_abort --target x86_64-unknown-linux-gnu --release"],
  },
  "format" => {
    "Darwin" => ["cargo fmt"],
    "Linux" => ["cargo fmt"],
  },
  "clean" => {
    "Darwin" => ["cargo clean"],
    "Linux" => ["cargo clean"],
  },
}
```
## But what do these variables mean?

The `GREET` variable is is the welcome message. This line is the first line that is printed by the build system.               
       
The `PROFILES` variable defines the list of your different profiles.       
      
The `COMMANDS` variable defines what commands the build system should run when the user requests a profile. It's a HashMap, also known as a dictionary.       

## Coolio, where do I store this configuration?
The build system will look for a ".keet" file storing this configuration and evaluate it accordingly. Place this file in the same position as parakeet.

## Fantastic, but what if I want a fancy configuration that can't just be fit like this?
Fear not my friend! The configuration is *comlpetely* turing complete as it is just Ruby code in the end! Parakeet will simply evaluate the file and you can use all the fancy Ruby code you want.
___

# License
This project is licensed under the MIT license.
