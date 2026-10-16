# VSeed S40 — experimental Home Assistant reference

Community materials shared by [@Od1n666](https://github.com/Od1n666) with [@dimitrilendi-tech](https://github.com/dimitrilendi-tech), [@lientry](https://github.com/lientry), and [@iamkaku](https://github.com/iamkaku) for [Issue #41](https://github.com/lientry/homeassistant-vivosun-growhub/issues/41).

## Files

- [vseed_s40_reference.patch](vseed_s40_reference.patch): **reference patch**, with the locally modified integration code added under `examples/`. Applying it does **not** install working native S40 support.
- [vseed_steckling_example.yaml](vseed_steckling_example.yaml): experimental Home Assistant package with a 14-day cutting propagation schedule. Requires matching VSeed S40 entities; adapt entity IDs for your setup.

## Developer review — applying the reference patch

```bash
git clone https://github.com/lientry/homeassistant-vivosun-growhub.git
cd homeassistant-vivosun-growhub
git checkout -b review/od1n666-vseed-s40
curl -L https://raw.githubusercontent.com/Od1n666/vseed-s40-propagation/main/vseed_s40_reference.patch -o vseed_s40_reference.patch
git apply --check vseed_s40_reference.patch
git apply vseed_s40_reference.patch
```

This adds **reference source only under `examples/`**. Existing upstream integration files are not modified. Review and selectively port relevant S40 functionality into the maintained upstream architecture. **This is not a drop-in installation patch.**

## Propagation example

Copy `vseed_steckling_example.yaml` to `/config/packages/vseed_steckling.yaml` only if Home Assistant packages are enabled and the local integration exposes the matching entities. Check all required helpers, entity IDs and behavior before enabling; this is an experimental example, not guaranteed to work unchanged.

Please share only **sanitized** VSeed field mappings/payload excerpts, not raw credentials or personal diagnostics.
