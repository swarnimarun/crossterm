# Version master

- Deprecated warning about `crossterm_*` crates
- Documentation improved
- Remove all references to the crossterm book
- Remove the crossterm book

# Version 0.11.1

- Maintenance release
- All sub-crates were moved to their own repositories in the `crossterm-rs` organization

# Version 0.11.0

As a preparation for crossterm 0.1.0 we have moved crossterm to an organisation called 'crossterm-rs'.

### Code Quality

- Code Cleanup: [warning-cleanup], [crossterm_style-cleanup], [crossterm_screen-cleanup], [crossterm_terminal-cleanup], [crossterm_utils-cleanup], [2018-cleanup], [api-cleanup-1], [api-cleanup-2], [api-cleanup-3]
- Examples: [example-cleanup_1], [example-cleanup_2], [example-fix], [commandbar-fix], [snake-game-improved]
- Fixed all broken tests and added tests 

### Important Changes

- Return written bytes: [return-written-bytes]
- Added derives: `Debug` for `ObjectStyle`  [debug-derive], Serialize/Deserialize for key events [serde]
- Improved error handling:
    - Return `crossterm::Result` from all api's: [return_crossterm_result]
         * `TerminalCursor::pos()` returns `Result<(u16, u16)>`
         * `Terminal::size()` returns `Result<(u16, u16)>`
         * `TerminalCursor::move_*` returns `crossterm::Result`
         * `ExecutableCommand::queue` returns `crossterm::Result`
         * `QueueableCommand::queue` returns `crossterm::Result`
         * `get_available_color_count` returns no result
         * `RawScreen::into_raw_mode` returns `crossterm::Result` instead of `io::Result`
         * `RawScreen::disable_raw_mode` returns `crossterm::Result` instead of `io::Result`
         * `AlternateScreen::to_alternate` returns `crossterm::Result` instead of `io::Result`
         * `TerminalInput::read_line` returns `crossterm::Result` instead of `io::Result`
         * `TerminalInput::read_char` returns `crossterm::Result` instead of `io::Result`     
         * Maybe I forgot something, a lot of functions have changed    
     - Removed all unwraps/expects from library
- Added KeyEvent::Enter and KeyEvent::Tab: [added-key-event-enter], [added-key-event-tab] 
- Synced set/get terminal size behaviour: [fixed-get-set-terminal-size]
- Method renames:
    * `AsyncReader::stop_reading()` to `stop()`
    * `RawScreen::disable_raw_mode_on_drop` to `keep_raw_mode_on_drop`
    * `TerminalCursor::reset_position()` to `restore_position()`
    * `Command::get_anis_code()` to `ansi_code()`
    * `available_color_count` to `available_color_count()`
    * `Terminal::terminal_size` to `Terminal::size`
    * `Console::get_handle` to `Console::handle`
- All `i16` values for indexing: set size, set cursor pos, scrolling synced to `u16` values
- Command API takes mutable self instead of self

[serde]: https://github.com/crossterm-rs/crossterm/pull/190

[debug-derive]: https://github.com/crossterm-rs/crossterm/pull/192
[example-fix]: https://github.com/crossterm-rs/crossterm/pull/193
[commandbar-fix]: https://github.com/crossterm-rs/crossterm/pull/204

[warning-cleanup]: https://github.com/crossterm-rs/crossterm/pull/198
[example-cleanup_1]: https://github.com/crossterm-rs/crossterm/pull/196
[example-cleanup_2]: https://github.com/crossterm-rs/crossterm/pull/225
[snake-game-improved]: https://github.com/crossterm-rs/crossterm/pull/231
[crossterm_style-cleanup]: https://github.com/crossterm-rs/crossterm/pull/208
[crossterm_screen-cleanup]: https://github.com/crossterm-rs/crossterm/pull/209
[crossterm_terminal-cleanup]: https://github.com/crossterm-rs/crossterm/pull/210
[crossterm_utils-cleanup]: https://github.com/crossterm-rs/crossterm/pull/211
[2018-cleanup]: https://github.com/crossterm-rs/crossterm/pull/222
[wild-card-cleanup]: https://github.com/crossterm-rs/crossterm/pull/224

[api-cleanup-1]: https://github.com/crossterm-rs/crossterm/pull/235
[api-cleanup-2]: https://github.com/crossterm-rs/crossterm/pull/238
[api-cleanup-3]: https://github.com/crossterm-rs/crossterm/pull/240

[return-written-bytes]: https://github.com/crossterm-rs/crossterm/pull/212

[return_crossterm_result]: https://github.com/crossterm-rs/crossterm/pull/232
[added-key-event-tab]: https://github.com/crossterm-rs/crossterm/pull/239
[added-key-event-enter]: https://github.com/crossterm-rs/crossterm/pull/236
[fixed-get-set-terminal-size]: https://github.com/crossterm-rs/crossterm/pull/242

# Version 0.10.1

# Version 0.10.0 ~ yanked
- Implemented command API, to have better performance and more control over how and when commands are executed. [PR](https://github.com/crossterm-rs/crossterm/commit/1a60924abd462ab169b6706aab68f4cca31d7bc2), [issue](https://github.com/crossterm-rs/crossterm/issues/171)
- Fixed showing, hiding cursor windows implementation
- Removed some of the parsing logic from windows keys to ansi codes to key events [PR](https://github.com/crossterm-rs/crossterm/commit/762c3a9b8e3d1fba87acde237f8ed09e74cd9ecd) 
- Made terminal size 1-based [PR](https://github.com/crossterm-rs/crossterm/commit/d689d7e8ed46a335474b8262bd76f21feaaf0c50)
- Added some derive implementation

# Version 0.9.6

- Copy for KeyEvent
- CTRL + Left, Down, Up, Right key support
- SHIFT + Left, Down, Up, Right key support
- Fixed UNIX cursor position bug [issue](https://github.com/crossterm-rs/crossterm/issues/140), [PR](https://github.com/crossterm-rs/crossterm/pull/152)

# Version 0.9.5

- Prefetching buffer size for more efficient windows input reads. [PR](https://github.com/crossterm-rs/crossterm/pull/144)

# Version 0.9.4

- Reset foreground and background color individually. [PR](https://github.com/crossterm-rs/crossterm/pull/138)
- Backtap input support. [PR](https://github.com/crossterm-rs/crossterm/pull/129)
- Corrected white/grey and added dark grey.
- Fixed getting cursor position with raw screen enabled. [PR](https://github.com/crossterm-rs/crossterm/pull/134)
- Removed one redundant stdout lock

# Version 0.9.3

- Removed println from `SyncReader`

## Version 0.9.2

- Terminal size linux was not 0-based
- Windows mouse input event position was 0-based ans should be 1-based
- Result, ErrorKind are made re-exported
- Fixed some special key combination detections for UNIX systems
- Made FreeBSD compile

## Version 0.9.1

- Fixed libc compile error

## Version 0.9.0 (yanked)

This release is all about moving to a stabilized API for 1.0.

- Major refactor and cleanup.
- Improved performance; 
    - No locking when writing to stdout. 
    - UNIX doesn't have any dynamic dispatch anymore. 
    - Windows has improved the way to check if ANSI modes are enabled.
    - Removed lot's of complex API calls: `from_screen`, `from_output`
    - Removed `Arc<TerminalOutput>` from all internal Api's. 
- Removed termios dependency for UNIX systems.
- Upgraded deps.
- Removed about 1000 lines of code
    - `TerminalOutput` 
    - `Screen`
    - unsafe code
    - Some duplicated code introduced by a previous refactor.
- Raw modes UNIX systems improved     
- Added `NoItalic` attribute

## Version 0.8.2

- Bug fix for sync reader UNIX.

## Version 0.8.1

- Added public re-exports for input.

# Version 0.8.0

- Introduced KeyEvents
- Introduced MouseEvents
- Upgraded crossterm_winapi 0.2

# Version 0.7.0

- Introduced more `Attributes`
- Introduced easier ways to style text [issue 87](https://github.com/crossterm-rs/crossterm/issues/87).
- Removed `ColorType` since it was unnecessary.

# Version 0.6.0

- Introduced feature flags; input, cursor, style, terminal, screen.
- All modules are moved to their own crate.
- Introduced crossterm workspace
- Less dependencies.
- Improved namespaces.

[PR 84](https://github.com/crossterm-rs/crossterm/pull/84)

# Version 0.5.5

- Error module is made public [PR 78](https://github.com/crossterm-rs/crossterm/pull/78).

# Version 0.5.4

- WinApi rewrite and correctly error handled [PR 67](https://github.com/crossterm-rs/crossterm/pull/67)
- Windows attribute support [PR 62](https://github.com/crossterm-rs/crossterm/pull/62)
- Readline bug fix windows systems [PR 62](https://github.com/crossterm-rs/crossterm/pull/62)
- Error handling improvement.
- General refactoring, all warnings removed.
- Documentation improvement.

# Version 0.5.1

- Documentation refactor.
- Fixed broken API documentation [PR 53](https://github.com/crossterm-rs/crossterm/pull/53).

# Version 0.5.0

- Added ability to pause the terminal [issue](https://github.com/crossterm-rs/crossterm/issues/39)
- RGB support for Windows 10 systems
- ANSI color value (255) color support
- More convenient API, no need to care about `Screen` unless working with when working with alternate or raw screen [PR](https://github.com/crossterm-rs/crossterm/pull/44)
- Implemented Display for styled object

# Version 0.4.3

- Fixed bug [issue 41](https://github.com/crossterm-rs/crossterm/issues/41)

# Version 0.4.2

- Added functionality to make a styled object writable to screen [issue 33](https://github.com/crossterm-rs/crossterm/issues/33)
- Added unit tests.
- Bugfix with getting terminal size unix.
- Bugfix with returning written bytes [pull request 31](https://github.com/crossterm-rs/crossterm/pull/31)
- removed methods calls: `as_any()` and `as_any_mut()` from `TerminalOutput`

# Version 0.4.1

- Fixed resizing of ansi terminal with and height where in the wrong order.

# Version 0.4.0

- Input support (read_line, read_char, read_async, read_until_async)
- Styling module improved
- Everything is multithreaded (`Send`, `Sync`)
- Performance enhancements: removed mutexes, removed state manager, removed context type removed unnecessarily RC types.
- Bug fix resetting console color.
- Bug fix whit undoing raw modes.
- More correct error handling.
- Overall commend improvement.
- Overall refactor of code.

# Version 0.3.0

This version has some braking changes check [upgrade manual](UPGRADE%20Manual.md) for more information about what is changed. 
I think you should not switch to version `0.3.0` if you aren't going to use the AlternateScreen feature.
Because you will have some work to get to the new version of crossterm depending on your situation. 

Some Features crossterm 0.3.0
- Alternate Screen for windows and unix systems.
- Raw screen for unix and windows systems [Issue 5](https://github.com/crossterm-rs/crossterm/issues/5)..
- Hiding an showing the cursor.
- Control over blinking of the terminal cursor (only some terminals are supporting this).
- The terminal state will be set to its original state when process ends [issue7](https://github.com/crossterm-rs/crossterm/issues/7).
- exit the current process.

## Alternate screen

This create supports alternate screen for both windows and unix systems. You can use 

*Nix style applications often utilize an alternate screen buffer, so that they can modify the entire contents of the buffer, without affecting the application that started them.
The alternate buffer is exactly the dimensions of the window, without any scrollback region.
For an example of this behavior, consider when vim is launched from bash.
Vim uses the entirety of the screen to edit the file, then returning to bash leaves the original buffer unchanged.

I Highly recommend you to check the `examples/program_examples/first_depth_search` for seeing this in action. 

## Raw screen

This crate now supports raw screen for both windows and unix systems. 
What exactly is raw state:
- No line buffering.
   Normally the terminals uses line buffering. This means that the input will be send to the terminal line by line.
   With raw mode the input will be send one byte at a time.
- Input
  All input has to be written manually by the programmer.
- Characters
  The characters are not processed by the terminal driver, but are sent straight through.
  Special character have no meaning, like backspace will not be interpret as backspace but instead will be directly send to the terminal.
With these modes you can easier design the terminal screen.

## Some functionalities added 

- Hiding and showing terminal cursor
- Enable or disabling blinking of the cursor for unix systems (this is not widely supported)
- Restoring the terminal to original modes.
- Added a [wrapper](https://github.com/crossterm-rs/crossterm/blob/master/src/shared/crossterm.rs) for managing all the functionalities of crossterm `Crossterm`.
- Exit the current running process

## Examples
Added [examples](https://github.com/crossterm-rs/crossterm/tree/master/examples) for each version of the crossterm version. 
Also added a folder with some [real life examples](https://github.com/crossterm-rs/crossterm/tree/master/examples/program_examples).

## Context

What is the `Context`  all about? This `Context` has several reasons why it is introduced into `crossterm version 0.3.0`.
These points are related to the features like `Alternatescreen` and managing the terminal state.

- At first `Terminal state`:

    Because this is a terminal manipulating library there will be made changes to terminal when running an process. 
    If you stop the process you want the terminal back in its original state. 
    Therefore, I need to track the changes made to the terminal. 
 
- At second `Handle to the console`

    In Rust we can use `stdout()` to get an handle to the current default console handle. 
    For example when in unix systems you want to print something to the main screen you can use the following code: 

        write!(std::io::stdout(), "{}", "some text").

    But things change when we are in alternate screen modes. 
    We can not simply use `stdout()` to get a handle to the alternate screen, since this call returns the current default console handle (handle to mainscreen).
    
    Because of that we need to store an handle to the current screen. 
    This handle could be used to put into alternate screen modes and back into main screen modes.
    Through this stored handle Crossterm can execute its command and write on and to the current screen whether it be alternate screen or main screen.
    
    For unix systems we store the handle gotten from `stdout()` for windows systems that are not supporting ANSI escape codes we store WinApi `HANDLE` struct witch will provide access to the current screen. 
    
So to recap this `Context` struct is a wrapper for a type that manges terminal state changes. 
When this `Context` goes out of scope all changes made will be undone.
Also is this `Context` is a wrapper for access to the current console screen.

Because Crossterm needs access to the above to types quite often I have chosen to add those two in one struct called `Context` so that this type could be shared throughout library. 
Check this link for more info: [cleanup of rust code](https://stackoverflow.com/questions/48732387/how-can-i-run-clean-up-code-in-a-rust-library). 
More info over writing to alternate screen buffer on windows and unix see this [link](https://github.com/crossterm-rs/crossterm/issues/17)

__Now the user has to pass an context type to the modules of Crossterm like this:__
      
      let context = Context::new();
      
      let cursor = cursor(&context);
      let terminal = terminal(&context);
      let color = color(&context);
    
Because this looks a little odd I will provide a type withs will manage the `Context` for you. You can call the different modules like the following:

      let crossterm = Crossterm::new();
      let color = crossterm.color();
      let cursor = crossterm.cursor();
      let terminal = crossterm.terminal();
     
      
### Alternate screen
When you want to switch to alternate screen there are a couple of things to keep in mind for it to work correctly. 
First off some code of how to switch to Alternate screen, for more info check the [alternate screen example](https://github.com/crossterm-rs/crossterm/blob/master/examples/alternate_screen.rs).

_Create alternate screen from `Context`_

        // create context.
        let context = crossterm::Context::new();
        // create instance of Alternatescreen by the given context, this wil also switch to it.
        let mut screen = crossterm::AlternateScreen::from(context.clone());        
        // write to the alternate screen.
        write!(screen,  "test");
        
_Create alternate screen from `Crossterm`:_

        // create context.
        let crossterm = ::crossterm::Crossterm::new();
        // create instance of Alternatescreen by the given refrence to crossterm, this wil also switch to it.
        let mut screen = crossterm::AlternateScreen::from(&crossterm);        
        // write to the alternate screen.
        write!(screen,  "test");
         
like demonstrated above, to get the functionalities of `cursor(), color(), terminal()` also working on alternate screen.
You need to pass it the same `Context` as you have passed to the previous three called functions,
If you don't use the same `Context` in `cursor(), color(), terminal()` than these modules will be using the main screen and you will not see anything at the alternate screen. If you use the [Crossterm](https://github.com/crossterm-rs/crossterm/blob/master/src/shared/crossterm.rs) type you can get the `Context` from it by calling the crossterm.get_context() whereafter you can create the AlternateScreen from it. 

# Version 0.2.2

- Bug see [issue 15](https://github.com/crossterm-rs/crossterm/issues/15)

# Version 0.2.1

- Default ANSI escape codes for windows machines, if windows does not support ANSI switch back to WinApi.
- method grammar mistake fixed [Issue 3](https://github.com/crossterm-rs/crossterm/issues/3)
- Some Refactorings in method names see [issue 4](https://github.com/crossterm-rs/crossterm/issues/4)
- Removed bin reference from crate [Issue 6](https://github.com/crossterm-rs/crossterm/issues/6)
- Get position unix fixed [issue 8](https://github.com/crossterm-rs/crossterm/issues/8)

# Version 0.2

- 256 color support. 
- Text Attributes like: bold, italic, underscore and crossed word ect. 
- Custom ANSI color code input to set fore- and background color for unix.
- Storing the current cursor position and resetting to that stored cursor position later. 
- Resizing the terminal.
