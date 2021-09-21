Release notes for Agda version 2.6.3
====================================

Syntax
------

* It is now OK to put lambda-bound variables anywhere in the
  right-hand side of a syntax declaration. However, there must always
  be at least one "identifier" between any two regular "holes". For
  instance, the following syntax declaration is accepted because `-`
  is between the holes `B` and `D`.

  ```agda
  postulate
    F : (Set → Set) → (Set → Set) → Set

  syntax F (λ A → B) (λ C → D) = B A C - D
  ```

* Syntax can now use lambdas with multiple arguments
  ([#394](https://github.com/agda/agda/issues/394)).

  Example:

  ```agda
  postulate
    Σ₂ : (A : Set) → (A → A → Set) → Set

  syntax Σ₂ A (λ x₁ x₂ → P) = [ x₁ x₂ ⦂ A ] × P
  ```
