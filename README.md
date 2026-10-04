# IPTV device and player compatibility (Canada)

An open dataset that lists, device by device, which IPTV player apps their developers say run on that device, which login methods those apps document, how they are installed, and the main limitation of each platform. Every record cites the first-party pages it was built from and the date it was last checked.

This is a machine-readable copy of the table published at:

**https://iptvcanadaneo.ca/iptv-device-compatibility-canada/**

That page is the canonical source. If this dataset and the page ever disagree, the page is the current version.

## Files

| File | Format |
|---|---|
| `iptv-device-compatibility-canada.json` | JSON array of 15 objects, UTF-8 |
| `iptv-device-compatibility-canada.csv` | CSV (RFC 4180), UTF-8 without BOM, comma-delimited, CRLF line endings, header row, 15 data rows |
| `LICENSE` | Creative Commons Attribution 4.0 International (legal code) |

Both data files contain the same 15 records with the same values, in the same order as the table on the source page.

## What the dataset covers

Fifteen device families sold or used in Canada:

1. Fire TV sticks on Vega OS
2. Fire TV sticks and Cube on Fire OS
3. Fire TV Edition televisions
4. Android TV / Google TV devices
5. Apple TV (tvOS)
6. iPhone and iPad
7. Samsung smart TVs (Tizen)
8. LG smart TVs (webOS)
9. VIDAA, Foxxum, Whale OS and Titan OS televisions
10. Roku players and Roku TVs
11. Formuler boxes
12. MAG set-top boxes (Infomir)
13. BuzzTV boxes
14. Windows PC
15. Mac

The dataset describes **player apps** (software that plays a playlist or portal the user already has). It does not list, rate or describe IPTV services, channels or content, and it does not rank apps.

## Fields

| JSON field | CSV column | Type | Description |
|---|---|---|---|
| `id` | `id` | integer | Row number, 1–15, in the order of the source table. |
| `status_tag` | `status_tag` | string | The tag class on the source row: `ok`, `lim` or `no`. It is a coarse visual grouping only; read `status_label` and `important_limitation` for what it means for that row. |
| `status_label` | `status_label` | string | The short label shown with the tag on the source row. Empty where the source row shows no label (rows 14 and 15). |
| `devices` | `devices` | string | The devices covered by the row, as named on the source page. |
| `platform_details` | `platform_details` | string | Operating system, version and, where published, model codes. |
| `compatible_players` | `compatible_players` | array of strings / pipe-joined string | Player apps the developer or store lists for this platform, with the developer's own wording in quotation marks where quoted. |
| `supported_login_methods` | `supported_login_methods` | array of strings / pipe-joined string | Login or playlist methods each app documents (for example M3U, Xtream Codes API, Stalker / Ministra portal, MAC-based upload). |
| `official_installation_route` | `official_installation_route` | string | The installation route the platform or developer documents. |
| `important_limitation` | `important_limitation` | string | The main caveat recorded for the row. |
| `sources` | `source_titles`, `source_urls` | array of `{title, url}` / two pipe-joined strings | The first-party pages behind the row. In CSV, the *n*-th title belongs to the *n*-th URL. |
| `last_verified` | `last_verified` | string, ISO 8601 date (`YYYY-MM-DD`) | The date the row was last checked against its sources. |

**List values.** In JSON, `compatible_players`, `supported_login_methods` and `sources` are always arrays. Where the source cell is a bulleted list, each list item is one array element. Where the source cell is a single sentence, the array has one element holding that sentence. Elements are not split further, so a single element may name several apps (for example, row 9's single login element `"Smart IPTV: M3U by MAC · SmartOne: Xtream-style API or M3U · HotPlayer, ibo Pro: M3U"`).

**CSV list encoding.** In CSV, array values are joined with ` | ` (space, vertical bar, space). The vertical bar does not occur anywhere in the data, so splitting on ` | ` restores the arrays exactly.

**Text.** Cell text is copied from the source page without rewording. Typographic characters (curly quotation marks, em and en dashes, `·`, `›`, `…`) are kept as UTF-8. There is no HTML markup in either file.

## Methodology and source policy

As stated on the source page, each value comes from one of three kinds of first-party source:

- **Manufacturer and platform documentation**, such as Amazon's Fire TV device table and Vega OS documentation, Roku's developer documentation, and the Formuler, Infomir and BuzzTV product pages.
- **The app developer's own website.**
- **Official store listings**: Google Play, the Canadian App Store, the Samsung and LG TV stores, and the Microsoft Store.

Reseller compatibility lists, press reports and forum posts are not used as values. Where press has reported something a manufacturer has not published, the table records only what the manufacturer says. Where a first-party source does not document something (for example a supported model-year range), the row says so instead of filling the gap.

Every record keeps its source URLs. They are the HTTPS URLs used on the source page, with no tracking parameters. Some store links carry locale parameters (`hl=en&gl=CA` on Google Play, `hl=en-CA&gl=CA` on the Microsoft Store) so that they open the English-language Canadian listing. Google Play links also carry the app's `id=` parameter, which identifies the listing.

## Verification dates

`last_verified` is per row. It records the last date someone checked that row against its listed sources, not the date the file was generated. In this release:

- Row 1 (Vega OS) was last verified on **2026-10-04**.
- Rows 2–15 were last verified on **2026-10-02**.

According to the source page, the table is re-checked every quarter and within a week of a device or operating-system announcement from Amazon, Google, Apple, Samsung or LG. A row changes only when a first-party page changes, and each change is recorded in the changelog on the source page.

## Limitations

- **Point-in-time snapshot.** App availability, store listings, supported OS versions and prices change without notice. Check the cited source before relying on a value.
- **Coverage is selective.** The dataset lists the apps and devices on the source table, not every IPTV player or every device on the market. An app missing from a row is not evidence that it does not run there.
- **Developer claims, not lab tests.** Values report what manufacturers, developers and stores publish. They are not the result of independent testing on each device or model.
- **Canadian context.** Store links point to Canadian storefronts. Availability can differ in other regions.
- **Ambiguous product names.** "Fire TV Stick HD" and "Fire TV Stick 4K" each name both a Fire OS and a Vega OS generation. Use the model codes in `platform_details` to tell them apart.
- **Publisher-specific wording.** The text is copied unchanged from a page maintained by an IPTV service provider. A few cells refer to that publisher or its website: row 10 states that the publisher's service does not support Roku and points to its setup hub. These statements describe the publisher's own service, not the Roku platform in general.
- **Prices.** Where a developer publishes a price, the row quotes it as published at the verification date (for example the one-time per-device fee in row 2, the App Store price in row 6). Prices are not tracked over time.
- **No endorsement.** Listing an app or device is not a recommendation, and nothing here is affiliated with or endorsed by the manufacturers, developers or stores named.

## Licence and attribution

The dataset's selection and arrangement of records and its original descriptive text are published under the **Creative Commons Attribution 4.0 International** licence ([CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)). See `LICENSE` for the full legal code.

Suggested attribution:

> IPTV device and player compatibility (Canada), IPTV Canada Neo, CC BY 4.0. Source: https://iptvcanadaneo.ca/iptv-device-compatibility-canada/

**What the licence does not cover:**

- **Facts.** Underlying facts (which app lists which platform, which login method an app documents, an OS version or model code) are not owned by the publisher. You may use them freely.
- **Third-party material.** Phrases quoted from developers, manufacturers and stores (shown in quotation marks), and the content of the linked source pages, belong to their respective owners. They are reproduced here as short quotations for reference and are not licensed by the publisher.
- **Trademarks.** Product, platform, app and company names are trademarks of their respective owners and are used only to identify the products described. As stated in section 2(b)(2) of the licence, trademark rights are not licensed.

## Publisher

Published and maintained by IPTV Canada Neo (https://iptvcanadaneo.ca/), which also maintains the source table. Corrections are welcome. Please open an issue with the row `id`, the value concerned and a link to the first-party page that shows the correct information.
