function Parent() {
  const [count, setCount] = useState(0);

  const handleClick = () => {
    console.log('Clicked');
  };

  return (
    <>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <Child onClick={handleClick} />
    </>
  );
}

function Child({ onClick }) {
  useEffect(() => {
    console.log('Child rendered');
  }, [onClick]);

  return <button onClick={onClick}>Child Button</button>;
}
Every time Parent re-renders (e.g., count increment), handleClick is redefined, causing a new function reference.

Since onClick prop changes (even though logic doesn’t), Child re-renders every time.

