# Badge Fix Notes

The "Made with Manus" badge is inside:
- `<manus-content-root>` (body > child)
  - shadow root
    - `<footer-watermark>` 
      - closed shadow root with the actual badge UI

CSS `display: none` on `manus-content-root` won't work because:
1. The deployed site uses a different build (not the dev server)
2. The badge is inside shadow DOM which is isolated from document styles
3. The CSS we added targets the host element, but the badge uses a closed shadow root

Solution: Use JavaScript in main.tsx to remove the element from DOM on mount.
