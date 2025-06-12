## Next.js App Router Course - Starter

This is the starter template for the Next.js App Router Course. It contains the starting code for the dashboard application.

For more information, see the [course curriculum](https://nextjs.org/learn) on the Next.js Website.

https://nextjs.org/learn/dashboard-app/getting-started

## `picture`、`source`

`next/image`に`picture`の仕組みはない。直接的に書くことはできる。

```
 <picture>
	<source
		media="(width >= 48rem)"
		srcSet="/hero-desktop.png"
	/>
	<img
		src="/hero-mobile.png"
		alt="Screenshots of the dashboard project showing mobile version"
	/>
</picture>
```

## `className`内で条件分岐

スペースを明示的に追加する必要がある。

```
className={'flex ' + (pathname === link.href && 'bg-sky-100 text-blue-600')}
```

## `await Promise.all`

複数の非同期処理（`Promise`）を並列で実行することが可能。

## ダイナミックレンダリング

基本は静的レンダリング。`fetch`、DBアクセス等があると自動的にダイナミックレンダリングになる。

`Suspense`を使うと、データ取得やコンポーネントの遅延読み込みなど「待ち時間」が発生する場面で、ローディング中に表示するUIを簡単に制御できる。

1. ページ レベルで、`loading.tsx`ファイル（`<Suspense>`自動的に作成されます）を使用します。
2. コンポーネント レベルでは、`<Suspense>`によりきめ細かな制御が可能です。

