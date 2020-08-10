# React Typescript

```typescript
import React, { useState, useRef } from "react";

interface Person {
  firstName: string;
  lastName: string;
}

interface Props {
  text: string;
  ok?: boolean; // ? Means optional
  i?: number;
  fn?: (bob: string) => string; // function that take in string and return string
  person: Person; // person that has typescript object Person
  handleChange: (event: React.ChangeEvent<HTMLInputElement>) => void;
}

interface TextNode {
  text: string;
}

export const TextField: React.FC<Props> = ({ handleChange }) => {
  const [count, setCount] = useState<TextNode>({ text: "hello" });
  // Passing the object of TextNode from interface
  
  const [number, setNumber] = useState<number | null | undefined | string>(0)
  // Means the number can be of type number OR null OR undefined OR string
      
  const inputRef = useRef<HTMLInputElement>(null);
  const divRef = useRef<HTMLDivElement>(null);
  
  // ***PRO TIPS: Use hover technique to tell you what type it is.

  return (
    <div ref={divRef}>
      <input ref={inputRef} onChange={handleChange} />
    </div>
  );
};
```

