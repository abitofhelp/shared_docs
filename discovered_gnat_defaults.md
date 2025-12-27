# Discovered GNAT Formatting Defaults
*Generated as part of the adafmt project - an Ada 2022 linter and formatter with AI-assisted repair.* 

**Version:** 1.0.0
**Date:** December 26, 2025
**SPDX-License-Identifier:** BSD-3-Clause<br>
**License File:** See the LICENSE file in the project root<br>
**Copyright:** © 2025 Michael Gardner, A Bit of Help, Inc.<br>
**Status:** Pre-Release

**Purpose:** Document GNAT formatting conventions discovered through empirical analysis of AdaCore source code for gap analysis.  Thesis: source code is written to standards and reviewed countless times, so it is the real style guide.

> "Trust the code, not the docs."

---

## Cheatsheet

Discovered GNAT defaults organized by category (alphabetized).

### Casing

| Field | Default | Description |
|-------|---------|-------------|
| `acronym_max_length` | 4 | Preserve short acronyms (GPS, LSP, IO) |
| `keyword` | lowercase | Ada keywords |
| `name` | Mixed_Case | Identifiers |
| `number` | Mixed_Case | Named numbers (not ALL_CAPS) |
| `type` | Mixed_Case | Type names |

### Comments

| Field | Default | Description |
|-------|---------|-------------|
| `align_trailing` | true | Align `--` on consecutive lines |
| `spaces_after_prefix` | 2 | `--  ` (two spaces) |
| `wrap` | true | Wrap at ~74-78 chars |

### Formatting

| Field | Default | Description |
|-------|---------|-------------|
| `based_grouping` | 4 | Hex: `16#DEAD_BEEF#` |
| `decimal_grouping` | 3 | Decimal: `1_000_000` |

### Indentation

| Field | Default | Description |
|-------|---------|-------------|
| `continuation` | 2 | Continuation line indent |
| `declaration_continuation` | 2 | After `:=` on new line |
| `kind` | spaces | Never tabs |
| `width` | 3 | Base indentation (GNAT standard) |

### Line

| Field | Default | Description |
|-------|---------|-------------|
| `break` | true | Break long lines |
| `width` | 79 | Max line length (headers use 78) |

### Spacing

| Field | Default | Description |
|-------|---------|-------------|
| `after_colons` | true | `Name : Type` |
| `after_commas` | true | `A, B, C` |
| `around_arrows` | true | `A => B` |
| `around_assignment` | true | `X := Y` |
| `around_operators` | true | `A + B` |
| `before_colons` | false | No space before `:` |
| `tabs_to_spaces` | true | Convert all tabs |

### Vertical Alignment

| Field | Default | Description |
|-------|---------|-------------|
| `assignments` | true | Align `:=` vertically |
| `comments` | true | Align `--` vertically |
| `declarations` | true | Align `:` vertically |

---

## Methodology

This document captures formatting conventions discovered by analyzing **actual GNAT source code** from official AdaCore repositories.

### Sources Analyzed

| Repository | Organization | Files Examined |
|------------|--------------|----------------|
| [ada_language_server](https://github.com/AdaCore/ada_language_server) | AdaCore | lsp-servers.adb/ads, lsp-ada_contexts.ads |
| [gnatstudio](https://github.com/AdaCore/gnatstudio) | AdaCore | gps-kernel.adb/ads, gps-kernel-messages.ads, string_utils.ads, gvd-types.ads |
| [Ada_Drivers_Library](https://github.com/AdaCore/Ada_Drivers_Library) | AdaCore | ak8963.adb, hal.ads, hal-bitmap.ads, stm32-gpio.ads, st7735r.ads |
| [gcc/ada](https://gcc.gnu.org/git/?p=gcc.git) | GNU/AdaCore | sinfo.ads |

**Total: 4 repositories, 14+ source files**

**Analysis Date:** December 2025

---

## Evidence Table

### Confidence Levels

| Level | Meaning |
|-------|---------|
| **HIGH** | Consistent across all 14+ files examined |
| **MEDIUM** | Consistent in most files, minor variations |

### Casing

| Field | Type | Evidence from Source Code | Default | Confidence |
|-------|------|---------------------------|---------|------------|
| `acronym_max_length` | integer | `GPS`, `LSP`, `VCS`, `MDI`, `UInt` preserved as-is | `4` | MEDIUM |
| `keyword` | string | All files use lowercase: `procedure`, `function`, `if`, `then` | `"lower"` | HIGH |
| `name` | string | `Get_Messages`, `Initialize`, `Load_Project`, `Parse_Header` | `"mixed"` | HIGH |
| `number` | string | `Screen_Width`, `Invalid_Address`, `No_Breakpoint` | `"mixed"` | HIGH |
| `type` | string | `Kernel_Handle`, `Message_Flags`, `ST7735R_Screen` | `"mixed"` | HIGH |

### Comments

| Field | Type | Evidence from Source Code | Default | Confidence |
|-------|------|---------------------------|---------|------------|
| `align_trailing` | boolean | Trailing comments aligned vertically in GPS and ALS | `true` | MEDIUM |
| `spaces_after_prefix` | integer | `--  ` format consistently used (two spaces after `--`) | `2` | HIGH |
| `wrap` | boolean | Long comments wrap to next line at approximately 74-78 characters | `true` | MEDIUM |

### Formatting

| Field | Type | Evidence from Source Code | Default | Confidence |
|-------|------|---------------------------|---------|------------|
| `based_grouping` | integer | `16#0001_0000#` shows 4-digit grouping in hex literals | `4` | MEDIUM |
| `decimal_grouping` | integer | `1_024`, `1_000_000` used for large decimal values | `3` | MEDIUM |

### Indentation

| Field | Type | Evidence from Source Code | Default | Confidence |
|-------|------|---------------------------|---------|------------|
| `continuation` | integer | Parameters align to `(` or use 2-3 space continuation indent | `2` | MEDIUM |
| `declaration_continuation` | integer | Lines after `:=` use 2-space indent consistently | `2` | MEDIUM |
| `kind` | string | Spaces used throughout all files, zero tab characters found | `"spaces"` | HIGH |
| `width` | integer | All files use exactly 3 spaces per indentation level | `3` | HIGH |

### Line

| Field | Type | Evidence from Source Code | Default | Confidence |
|-------|------|---------------------------|---------|------------|
| `break` | boolean | Long lines are broken at logical points consistently | `true` | HIGH |
| `width` | integer | Header comments use 78 chars, code stays within 79 | `79` | HIGH |

### Spacing

| Field | Type | Evidence from Source Code | Default | Confidence |
|-------|------|---------------------------|---------|------------|
| `after_colons` | boolean | `Name : Type` pattern with space after colon | `true` | HIGH |
| `after_commas` | boolean | `A, B, C` pattern with space after each comma | `true` | HIGH |
| `around_arrows` | boolean | ` => ` with spaces on both sides consistently | `true` | HIGH |
| `around_assignment` | boolean | ` := ` with spaces on both sides consistently | `true` | HIGH |
| `around_operators` | boolean | `X + Y`, `A - B` with spaces around operators | `true` | HIGH |
| `before_colons` | boolean | No space before `:` in any declaration observed | `false` | HIGH |
| `tabs_to_spaces` | boolean | Zero tab characters found across all 14+ files | `true` | HIGH |

### Vertical Alignment

| Field | Type | Evidence from Source Code | Default | Confidence |
|-------|------|---------------------------|---------|------------|
| `assignments` | boolean | `:=` operators aligned vertically in GPS kernel code | `true` | MEDIUM |
| `comments` | boolean | `--` aligned on consecutive end-of-line comments | `true` | MEDIUM |
| `declarations` | boolean | Colons aligned vertically in parameter lists | `true` | HIGH |

---

## Comparison: Style Guides vs Actual Code

**Legend:** ✓ = Match | ~ = Partial | - = Not in guide

### Casing

| Field | Style Guide | Actual Code | Match |
|-------|-------------|-------------|-------|
| `acronym_max_length` | Not specified | 4 chars | - |
| `keyword` | lowercase | lowercase | ✓ |
| `name` | Mixed_Case | Mixed_Case | ✓ |
| `number` | varies | Mixed_Case | ~ |
| `type` | Mixed_Case | Mixed_Case | ✓ |

### Comments

| Field | Style Guide | Actual Code | Match |
|-------|-------------|-------------|-------|
| `align_trailing` | Not specified | true | - |
| `spaces_after_prefix` | 2 spaces | 2 spaces | ✓ |
| `wrap` | Not specified | true (~74-78) | - |

### Formatting

| Field | Style Guide | Actual Code | Match |
|-------|-------------|-------------|-------|
| `based_grouping` | Not specified | 4 digits | - |
| `decimal_grouping` | Not specified | 3 digits | - |

### Indentation

| Field | Style Guide | Actual Code | Match |
|-------|-------------|-------------|-------|
| `continuation` | Not specified | 2 spaces | - |
| `declaration_continuation` | Not specified | 2 spaces | - |
| `kind` | spaces | spaces | ✓ |
| `width` | 3 spaces | 3 spaces | ✓ |

### Line

| Field | Style Guide | Actual Code | Match |
|-------|-------------|-------------|-------|
| `break` | Yes | Yes | ✓ |
| `width` | 79 chars | 79 chars | ✓ |

### Spacing

| Field | Style Guide | Actual Code | Match |
|-------|-------------|-------------|-------|
| `after_colons` | space after | space after | ✓ |
| `after_commas` | space after | space after | ✓ |
| `around_arrows` | spaces | spaces | ✓ |
| `around_assignment` | spaces | spaces | ✓ |
| `around_operators` | spaces | spaces | ✓ |
| `before_colons` | Not specified | false | - |
| `tabs_to_spaces` | no tabs | no tabs | ✓ |

### Vertical Alignment

| Field | Style Guide | Actual Code | Match |
|-------|-------------|-------------|-------|
| `assignments` | Not specified | true | - |
| `comments` | Not specified | true | - |
| `declarations` | Not specified | true | - |

---

## Key Findings

### 1. Colon Spacing: After Only

**Observed:** `Name : Type` (space after colon, not before)

```ada
--  Correct (GNAT style):
Handle           : out Kernel_Handle;
Application      : not null access Gtk_Application_Record'Class;

--  NOT observed:
Handle : out Kernel_Handle;   --  (space before colon - not GNAT style)
```

### 2. Digit Grouping: Used for Large Values

**Observed:** Underscores used when values exceed typical readability threshold.

```ada
--  Decimal grouping (3 digits):
Processing_Task_Stack_Size : constant := 32 * 1_024 * 1_024;

--  Hex grouping (4 digits):
Lock_Key : constant := 16#0001_0000#;
```

### 3. Continuation Indentation: 2 Spaces or Align to Parenthesis

**Observed:** Two patterns, both acceptable:

```ada
--  Pattern A: Align to opening parenthesis
procedure Gtk_New
  (Handle           : out Kernel_Handle;
   Application      : not null access Gtk_Application_Record'Class;

--  Pattern B: 2-space continuation
Side_And_Locations : constant Message_Flags :=
  (Editor_Side => True, Locations => True, others => False);
```

### 4. Named Constants: Mixed_Case (Not ALL_CAPS)

**Observed:** Constants use Mixed_Case with underscores, not SCREAMING_SNAKE_CASE.

```ada
--  GNAT style:
Screen_Width    : constant := 128;
Invalid_Address : constant Address_Type := ...;
No_Breakpoint   : constant := ...;

--  NOT typical GNAT style:
SCREEN_WIDTH : constant := 128;   --  (ALL_CAPS less common)
```

**Note:** Some embedded/hardware code uses ALL_CAPS for register constants, but Mixed_Case dominates in general GNAT code.

### 5. Line Width: 79 Characters

**Observed:** Code stays within 79 characters. Header comments use 78 characters for centered text.

```ada
--                               GNAT Studio                                --
--  ^-- 78 characters of dashes --^
```

### 6. Comment Prefix: Two Spaces After `--`

**Observed:** Consistently `--  ` (two spaces) for regular comments.

```ada
--  This is the standard GNAT comment format with two spaces.
--  Continuation lines maintain the same format.
```

### 7. Vertical Alignment: Widely Used

**Observed:** Colons, assignments, and comments aligned vertically on consecutive lines.

```ada
--  Parameter declarations:
Self     : not null access constant Messages_Container'Class;
Category : VSS.Strings.Virtual_String;
File     : GNATCOLL.VFS.Virtual_File

--  Assignments:
History_File_Base_Name : constant String  := "histories.xml";
History_Max_Length     : constant Positive := 10;
```

### 8. No Tabs

**Observed:** Zero tab characters across all analyzed files. Spaces only.

---

*Generated as part of the adafmt project - an Ada 2022 linter and formatter with AI-assisted repair.*
