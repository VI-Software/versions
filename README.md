# Versions (for VI Software Launcher)

Simple system for managing launcher version compatibility via a GitHub repository.

## How It Works

1. Check if version is in `supported` list --> ✅ Allow, no force update
2. Check if version is in `deprecated` list --> ✅ Allow, just show a warning
3. **Version not found anywhere OR below `minimumRequired` --> ❌ Force update**

## Version Patterns

| Pattern | Matches |
|---------|---------|
| `2.2.0` | Exact version |
| `2.2.*` | All 2.2.x versions |
| `^2.1.0` | >=2.1.0 <3.0.0 |
| `~2.1.0` | >=2.1.0 <2.2.0 |
| `>=2.0.0` | All versions >= 2.0.0 |

## How It Works

1. API fetches `versions.json` from this repo
2. Results are cached for 1 hour
3. When someone pushes changes, GitHub Actions calls the refresh endpoint
4. Cache clears immediately, next request gets fresh data