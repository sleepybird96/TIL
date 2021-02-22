# 타입스크립트로 구현해본 스택

```ts
type Data = {};

interface Stack {
	readonly size: number;
	push(value: string): void;
	pop(): string;
	getData(): Data;
}

class StackClass implements Stack {
	private data: Data = {};
	size: number = 0;

	getData(): Data {
		return this.data;
	}

	push(value: string): void {
		this.data[this.size] = value;
		this.size++;
	}

	pop(): string {
		if (!this.size) throw new Error("Nothing to pop");
		const popped: string = this.data[this.size - 1];
		delete this.data[this.size - 1];
		this.size--;
		return popped;
	}
}
```
