# Pull request draft - not submitted

Title: chore(assets): add twenty Australian birds from historical plates

These twenty species have existing BirdNET labels and body-mass entries but no artwork in the checked revision. This adds historical illustrations to Classic, including common Australian garden and urban birds.

Birds: Rainbow Lorikeet, Rose Robin, Laughing Kookaburra, Magpie-lark, Superb Fairywren, Yellow-faced Honeyeater, Crimson Rosella, Brown Thornbill, Olive-backed Oriole, Little Wattlebird, Australian Magpie, Sulphur-crested Cockatoo, Galah, Noisy Miner, Common Myna, Australian White Ibis, Crested Pigeon, Red Wattlebird, Tawny Frogmouth and Yellow-tailed Black-Cockatoo.

Nineteen illustrations come from Gould's *The Birds of Australia*, credited per plate to John and Elizabeth Gould or John Gould and Henry Constantine Richter. The myna is by John Gerrard Keulemans in Legge's *A History of the Birds of Ceylon*. The scans and transcriptions come from Smithsonian Libraries/Biodiversity Heritage Library, the University of Kansas, and Project Gutenberg/Internet Archive, as individually recorded. Source-rights statements and exact plate links are included in the review pack.

The change is twenty WebP files, twenty manifest entries and the necessary work-level attribution. Existing Classic terms are retained. Preparation uses conventional masking, proportional resizing and flat paper backing for the stock renderer, followed by unchanged `tools/add_bird.py` preparation and q90 WebP encoding with lossless alpha. The Tawny Frogmouth is cut closely around its original visible legs, toes and claws, removing the broad stump without reconstructing hidden anatomy. Codex assisted research, tooling and review; no bird pixels were generated or repainted. Application code and dependencies are unchanged.

The magpie uses a complete independent scan with its entire wing and tail. The myna preserves the original yellow facial skin and depicts the darker Sri Lankan subspecies, *Acridotheres tristis melanosternus*; it is not claimed to be a Sydney specimen. The Noisy Miner also has a regional-form qualification. The lorikeet preserves its overlapping pair. Small paper rims and authentic perch fragments remain documented.

All final images have reviewed 760-pixel previews. Three complete compositions were inspected in paper and six-colour software output, including a comparison with existing Classic artwork. The frogmouth's final encoding and four affected compositions were reviewed after its feet were recut; the other nineteen individual previews and two mixed compositions retain their exact reviewed bytes. No physical panel test has been performed.

Validation against `11b54d2884a857702284d1e3fc2629b6c655bc79`:

- Current revision: all four artwork name, mass, manifest and attribution tests pass, as does `git diff --check`.
- Current revision: the binary patch applies to clean pinned-baseline files and reproduces all 22 proposed file hashes. The other nineteen images, manifest and attribution are unchanged from the previous preparation. Package checksums, links and ZIP integrity pass.
- Carried-forward results from the previous preparation: Ruff formatting and lint checks passed, and Linux-target static type checking passed. Native Windows type checking retained two baseline Unix-signal errors. These checks were not rerun for the frogmouth-only image change.
- Carried-forward full Windows suite from the previous preparation: 369 passed and 15 failed, exactly matching the unchanged baseline failure set. These failures concern Unix date formatting and signal handling. The full suite was not rerun for the revised frogmouth image; its prior log and report are preserved separately.
- Linux runtime CI, physical panel output and ShellCheck remain untested locally. Shell scripts are unchanged. No test skips or application-code workarounds were introduced.

The larger local Sydney research collection and its optional generated illustrations are outside this PR.
