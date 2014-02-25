1. Make use of `describe`, `context`, `before` and `it` accordingly.
2. Prefer `expect` over `should` syntax. [source](http://betterspecs.org/#expect)
3. Use `let` for variables declaration. [source](http://betterspecs.org/#let)
4. Avoid declaring instance variables.
5. Use [factories](https://github.com/thoughtbot/factory_girl/blob/master/GETTING_STARTED.md).
6. Avoid hitting external services by mocking them or use its test helpers instead.
7. Record external HTTP interactions. [source](http://betterspecs.org/#http)
8. Use Capybara instead of Cucumber for integration tests.
