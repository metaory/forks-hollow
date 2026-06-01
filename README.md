<div align="center">
    <img src=".github/assets/logo.svg" alt="demo" height="128" />
    <h4>forks-hollow</h4>
    <p>
        Keep your fork tree layout
        <br>
        Drop the weight
        <br>
        Restore when you need the code
    </p>
</div>

---

## Why

I kept **500+ cloned repositories** in a hand-built tree: top-level buckets like `+UI`, `+ZSH`, `+DOC`, with nested `+`-prefixed categories inside (e.g. `+UI/+UI-LIB/...`). Each leaf was a normal git clone. The layout was meaningful; the disk use was not **gigabytes** for repos I rarely touch.

I still wanted the same paths, remotes, and README context. I did not want full checkouts sitting on disk all the time.

## What it does

**Hollow** a clone forest into a separate directory:

- **Same directory structure** as the source tree
- Each repo keeps `**.git`** and `**README.md**` only; everything else is stripped
- Result is typically **a few megabytes** instead of gigabytes

Two CLI tools:


| Command         | Role                                                                  |
| --------------- | --------------------------------------------------------------------- |
| `hollow-index`  | Scan nested clones, write hollow copies to `-o`                       |
| `hollow-unpack` | Walk hollow repos, `fetch` + checkout latest default branch into `-o` |


## Usage

```bash
hollow-index -i /path/to/full-clones -o /path/to/hollow
hollow-unpack -i /path/to/hollow -o /path/to/restored
```

Both take `-i` / `--input` and `-o` / `--output`. Structure is preserved end-to-end.

## Roadmap

- Selective unpack (one repo or subtree) instead of restoring everything in one run

---

## License

[MIT](LICENSE)
