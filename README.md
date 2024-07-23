# 2024React-Next

# Get git working
Put the following in .bash_profile   
   PATH="/usr/bin/git:$PATH"   
Run   
   xcode-select --install  
   
# 2024 React-Next Course
https://www.udemy.com/course/the-ultimate-react-course/learn/lecture/35882526#overview

# App.js code for Section 1.2 -  code is also at https://codesandbox.io/s/react-first-app-advice-52879f
Set up a code sandbox with my Google account credentials

import { useEffect, useState } from "react";

export default function App() {
  const [advice, setAdvice] = useState("");
  const [count, setCount] = useState(0);

  async function getAdvice() {
    const res = await fetch("https://api.adviceslip.com/advice");
    const data = await res.json();
    setAdvice(data.slip.advice);
    setCount((c) => c + 1);
  }

  useEffect(function () {
    getAdvice();
  }, []);

  return (
    <div>
      <h1>{advice}</h1>
      <button onClick={getAdvice}>Get advice</button>
      <Message count={count} />
    </div>
  );
}

function Message(props) {
  return (
    <p>
      You have read <strong>{props.count}</strong> pieces of advice
    </p>
  );
}
