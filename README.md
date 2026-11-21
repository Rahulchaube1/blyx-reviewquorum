<img src="assets/logo.png" width="112" height="112" alt="ReviewQuorum logo">

# ReviewQuorum

Count independent reviewers and calculate outstanding approvals. This Blyx library is part of the publishing and commerce collection.

A scheduled revision can reach its start time while a second approval is still missing. Track both conditions against the same clock. [Wagtail, scheduled publishing](https://guide.wagtail.org/en/concepts/scheduled-publishing/)

## Install and run

Install [Blyx 0.2.1](https://www.blyx-lang.space/download) with a Rust toolchain and host linker for native builds.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-reviewquorum.git
cd blyx-reviewquorum
blyxc native-run example.blyx
blyxc native-run tests.blyx
```

[Run the editable browser example](https://www.blyx-lang.space/play?example=package-reviewquorum) · [Package page](https://www.blyx-lang.space/packages/reviewquorum) · [Handbook](https://doc.blyx-lang.space/guide/oriole)

## Import the module

Run this in the directory containing your application's entry file.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-reviewquorum.git vendor/reviewquorum
```

```blyx
use vendor::reviewquorum::reviewquorum;

fn main() {
    let reviewers = [7, 7, 9];
    let required = 3.0;
    let result = reviewquorum_tally(reviewers, required);
    if len(result) == 0 { println!("invalid"); return; }
    let mut i = 0;
    while i < len(result) {
        println!(at(result, i));
        i += 1;
    }
}
```

Expected output

```text
2
1
```

## API

`reviewquorum_tally(reviewers, required)`

Returns [unique reviewer IDs, approvals still required]. A repeated ID contributes once. Invalid arguments and nonfinite results return an empty vector. Integers carried in numeric vectors use the exact range from −(2^53−1) to 2^53−1.

| Argument | Domain |
| --- | --- |
| reviewers | Vector of values, each a nonnegative exact integer |
| required | A positive exact integer |

## In use

[Oriole](https://github.com/Rahulchaube1/blyx-oriole) uses this module to decide whether a scheduled revision can go live after independent review.

## Verification and contributions

The regression suite in [tests.blyx](tests.blyx) checks the example, boundary cases and invalid inputs. Include a short reproducer and your compiler version in [an issue](https://github.com/Rahulchaube1/blyx-reviewquorum/issues). The source is dual-licensed under [MIT](LICENSE-MIT) or [Apache-2.0](LICENSE-APACHE). The package artwork uses [Lucide icons](https://lucide.dev/license); see [artwork notices](assets/NOTICE.txt).

## Connect with Rahul Chaube

[Portfolio](https://www.rahulchaube1.com/) · [GitHub](https://github.com/Rahulchaube1) · [LinkedIn](https://www.linkedin.com/in/rahulchaube1) · [Hugging Face](https://huggingface.co/oncody) · [X](https://x.com/RahulChaube_) · [EverestQ](https://www.everestqai.com/) · [Contact](https://www.rahulchaube1.com/contact)

[Blyx website](https://www.blyx-lang.space/) · [BlyxTorch](https://www.blyx-lang.space/packages/blyxtorch) · [Handbook](https://doc.blyx-lang.space/) · [Community](https://www.blyx-lang.space/community)

Support Rahul’s open-source work through [GitHub Sponsors](https://github.com/sponsors/Rahulchaube1) or [Buy Me a Coffee](https://buymeacoffee.com/rahulchaube).
