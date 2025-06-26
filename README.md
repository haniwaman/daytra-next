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

## PPR（部分事前レンダリング）

Next 15でまだ標準化されていない。

## Supabase

Supabaseは一定期間アクセスがないと自動的に一時停止になる模様。

```
Status:
Project has been paused. Go to Supabase Dashboard in order to unpause it.
```

90日以上一時停止されている場合は、完全にデータが消えそうです。

```
Free projects cannot be restored through the dashboard if they are paused for more than 90 days. The latest that your project can be restored is by 18 Sep 2025. However, your database backup and Storage objects will still be available for download thereafter.
```

Vercel → Storage → Supabase → Open in Supabase → Restore project で再稼働できる。

## URL関連のオブジェクト

- `import { useSearchParams, usePathname, useRouter } from 'next/navigation';`
	- `useSearchParams`・・・クエリパラメーターの取得
	- `usePathname`・・・パス名の取得（例：`/dashboard/invoices`）
	- `useRouter`の`replace`・・・ページをリロードせずにURLだけを変更するための関数
- `new URLSearchParams`・・・URLのクエリパラメーターを簡単に操作できるJavaScriptの組み込みオブジェクト

## デバウンス

デバウンスは、特定のイベントが頻繁に発生するのを抑制し、一定時間内に最後に発生したイベントだけを処理するためのテクニックです。例）ユーザーが入力を止めてから0.3秒後に検索処理が実行される