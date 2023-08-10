## Composing Client and Server Components

**\_ app/page.tsx **\_
\_Import cả hai client components và server components và bên trong một Server Components
```
import Contact from './contact/page'
import About from './about/page'
export default function Home() {
return (

<main>
<h1>Home</h1>
<Contact />
<About />
</main>
);
}
```

**\_ contact/page.tsx **\_
```
"use client";
export default function Contact() {
return <h1>Contact</h1>;

}
```

**\_ about/page.tsx **\_
```
export default function About() {
return <h1>About</h1>;
}
```

## Unsupported Pattern: Importing Server Components into Client Components (Using Props)

\_ Có thể truyền server component vào client componet bằng cách sử dụng props hoặc child
**\_ contact/page.tsx **\_
```
"use client";
export default function Contact({
children,
}: {
children: React.ReactNode
}) {
return <div>

<h1>Contact</h1>;
    {children}
</div> 
}
```

**\_ about/page.tsx **\_
```
export default function About() {
return <h1>About</h1>;
}
```

**\_ app/page.tsx **\_

```
import Contact from './contact/page'
import About from './about/page'
export default function Home() {
return (

<main>
<h1>Home</h1>
<Contact />
<About />
</Contact >
</main>
);
}
```
## Passing props from Server to Client Components

**\_ contact/page.tsx **\_
```
"use client";
export default function Contact({
data,
}: {
children: React.ReactNode
}) {
return <div>

<h1>Contact</h1>;
  <p>{data}</p>
</div> 
}
```

**\_ about/page.tsx **\_
```
export default function About() {
return <h1>About</h1>;
}
```
**\_ app/page.tsx **\_

```
import Contact from './contact/page'
import About from './about/page'
export default function Home() {
const renderData= 'render data';
return (

<main>
<h1>Home</h1>
<Contact props={renderData}/>
<About />
</Contact >
</main>
);
}
```

## Routing

**\_ contact/page.tsx **\_
```
export default function Contact () {
return <h1>Contact</h1>
}
```
**\_ about/page.tsx **\_
```
export default function About () {
return <h1>About</h1>
}
```
**\_ app/page.tsx **\_

```
import Link from 'next/link';

export default function App() {
return (

<Link href="/about">
<p>About</p>
</Link>
<Link href="/contact">
<p>Contact</p>
</Link>
);
}
```

## Routes Groups

**\_ Cấu trúc thư mục **\_

- app
  - about
    - page.tsx
  - contact
    - page.tsx
    - me
      - page.tsx
  - page.tsx

**\_ app/page.tsx **\_

```
import Link from 'next/link';

export default function App() {
return (

<Link href="/about">
<p>About</p>
</Link>
<Link href="/contact/me">
<p>Me</p>
</Link>
);
}
```
## Dynamic Routes

**\_ Cấu trúc thư mục **\_

- app
  - about
    - page.tsx
  - contact
    - page.tsx
    - me
      - page.tsx
      - [meId]
        - page.tsx
  - page.tsx
```
    import Link from 'next/link';

export default function App() {
return (

<Link href="/about">
<p>About</p>
</Link>
<Link href="/contact/[meId]/">
<p>Me Id</p>
</Link>
);
}
```
