# স্বাদঘর মসলা হাউজ — PWA starter files

এই ফোল্ডারে PWA-এর প্রাথমিক ফাইল আছে:
- `manifest.webmanifest`
- `sw.js`
- `icons/` (192px ও 512px আইকন)

## GitHub repository-তে যোগ করার নিয়ম
1. ZIP extract করুন।
2. GitHub-এ `imranhawlader8685-imran/sawdghor-masala` repository খুলুন।
3. `Add file` → `Upload files` চাপুন।
4. `manifest.webmanifest`, `sw.js`, এবং `icons` ফোল্ডারের ফাইলগুলো repository root-এ আপলোড করুন।
5. Commit changes করুন।

## index.html-এ সংযোজন
`<head>` ট্যাগের ভেতরে, `</head>`-এর আগে যোগ করুন:

```html
<link rel="manifest" href="./manifest.webmanifest">
<meta name="theme-color" content="#174b35">
<meta name="mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="default">
<link rel="icon" href="./icons/icon-192.png">
```

`</body>`-এর ঠিক আগে যোগ করুন:

```html
<script>
  if ("serviceWorker" in navigator) {
    window.addEventListener("load", () => {
      navigator.serviceWorker.register("./sw.js")
        .catch((error) => console.error("PWA service worker:", error));
    });
  }
</script>
```

**গুরুত্বপূর্ণ:** আপনার সাইট যদি GitHub Pages-এর HTTPS ঠিকানায় চলে, তাহলে Chrome-এ ইনস্টলযোগ্য হওয়ার প্রয়োজনীয় secure-origin শর্ত পূরণ হবে। `index.html`-এ আগে থেকেই একই manifest বা service worker registration থাকলে duplicate যোগ করবেন না।

## পরীক্ষা
আপডেট প্রকাশ হওয়ার পর Chrome-এ সাইট খুলুন → তিন ডট মেনু → `Install app` অথবা `Add to Home screen`। Chrome-এ ইনস্টল অপশন আসতে কিছু সময় লাগতে পারে।
