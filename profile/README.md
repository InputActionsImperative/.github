# InputActions Imperative
> [!CAUTION]
> While this project is open-source, its purpose is to fulfill **my** needs regarding input, not other users'. As a consequence, there is a set of rules to
> ensure that working on this project remains enjoyable for me:
> - feature requests will be rejected if I do not find them useful for myself or enjoyable to work on,
> - any pull requests implementing features which do not satisfy the aforementioned criteria will be rejected, as it would be my responsibility to maintain the
>   code later on,
> - breaking changes will be introduced frequently (since I cannot make up my mind regarding the API),
> - existing features may be removed at any time,
> - no stable releases will be made,
> - only the latest compositor version will be supported, though the project may still work with older versions as long as no breaking changes have been
>   made.
>
> The above rules are not strict and exceptions can be made.
>
> Bug reports and questions are still welcome.

Scriptable Linux utility for processing libinput/evdev events, a continuation of the original [InputActions](https://github.com/InputActions) project but
without declarative configuration.

## But why?
<details>
  <summary>stuff no one cares about</summary>

  In the original project, the user would only describe their desired configuration in YAML and InputActions would take care of the actual implementation.
  ```yaml
  touchpad:
    gestures:
      - type: swipe
        direction: right
        fingers: 3

        actions:
          - on: begin
            input:
              - command: dolphin
  ```

  The problem with such declarative configuration is that eventually someone will want something more complex
  (e.g. triggers with actions that execute on update events), and then it becomes my responsibility to implement it, otherwise such configurations will never be
  possible. Fast-forward a few years and now there are dozens of features I have to ensure work properly, and yet there are still tons of feature requests,
  each one requiring more work than the previous one.

  Sure, I could just use AI for all the boring stuff, but since I do not have unlimited free time, I would rather just not waste any of it at all and focus on
  manually coding things I enjoy (I like writing code, not prompts).

  InputActions Imperative shifts the responsibility of implementation to the end user, requiring them to write all the logic themselves in JavaScript/TypeScript,
  while InputActions only handles the low-level things, such as getting input events from the compositor and exposing them through the scripting API.

  I have decided to make it a separate project so that I can throw out all of the old, terrible, buggy code and never worry about it again without people
  getting mad at me for removing 99% of features.
</details>
