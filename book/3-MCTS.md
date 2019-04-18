# Monte Carlo Tree Search

## Min-max trees

## Monte Carlo Tree Search

```rust
pub trait Game<A: GameAction> : Clone {

    /// Return a list with all allowed actions given the current game state.
    fn allowed_actions(&self) -> Vec<A>;

    /// Change the current game state according to the given action.
    fn make_move(&mut self, action: &A);

    /// Reward for the player when reaching the current game state.
    fn reward(&self) -> f32;

    /// Derterminize the game
    fn set_rng_seed(&mut self, seed: u32);
}
```
