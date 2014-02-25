1. Avoid multiple assignments per line (one, two = 1, 2).
2. Avoid organizational comments (# Validations).
3. Avoid inline comments.
4. Avoid ternary operators (boolean ? true : false). Use multi-line if instead to emphasize code branches.
5. Avoid explicit return statements.
6. Avoid using semicolons.
7. Avoid bang (!) method names. Prefer descriptive names.
7. Avoid explicit `return`.
8. Don't use self explicitly anywhere except class methods (def self.method) and assignments (self.attribute =).
9. Prefer map over collect.
10. Use `&&` and `||` for Boolean expressions.
11. Use {...} for single-line blocks. Use do..end for multi-line blocks.
12. Use CamelCase for classes and modules, snake_case for variables and methods, SCREAMING_SNAKE_CASE for constants.
13. Use def self.method, not def Class.method or class << self.
14. Use def with parentheses when there are arguments.
15. Use each, not for, for iteration.
