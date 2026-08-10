# No Hardcoded Data

**A person must never see data they did not create or that does not exist in the real source of truth.** If the UI shows four members and the identity provider shows one, that is a bug: the system is lying. Born from a real incident where a settings page showed member rows that had drifted from the auth provider and from a dev-vs-prod instance mismatch.

Always on, every project. Layers with No-BS Mode.

## The rule

1. **Every user-visible value has a real source.** A name, email, count, list, status, or row shown to a person traces back to a real DB write (a real sign-in, booking, submission) or an authenticated API. Never to a literal you typed.
2. **No seed, mock, or placeholder data on any shared or production deployment.** No `const DEMO_USERS = [...]`, no hand-inserted rows, no faked counts. Demo data lives only on a throwaway local deployment and is never pushed where a real user can reach it.
3. **Derived stores reconcile with their source of truth.** A table mirroring an external source (a `members` table mirroring your auth provider) must prune rows whose source record no longer exists and add ones that do. A lazily-populated, never-pruned cache is a drift bug waiting to be discovered by a customer.
4. **One environment, one source.** Never point a production surface at a development identity instance (a `pk_test_` key serving real users). Dev data and prod data never share a deployment.
5. **Example data must be obviously fake and impossible to ship.** Gate it behind a dev-only flag, name it `__EXAMPLE__`, and add a CI check that fails if it appears in a production build.

## The three postures

**Writing a feature that renders data:** wire the list to the real query from the start; render an honest empty state if the backend is not ready. Never ship a hardcoded array of names to fill space.

**Reviewing a diff:** grep for arrays of names, emails, or ids; for `seed`, `mock`, `demo`, `placeholder`, `Lorem`; for literal counts. Any of these reaching a real surface is a blocking finding.

**Investigating a mismatch** ("the count is wrong", "there are records I did not create"): compare the displayed data to the true source (auth provider, DB rows). A mismatch is a drift, seed, or wrong-instance bug. **Fix the source-of-truth connection; never patch the display to hide the gap.**
