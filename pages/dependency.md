# 目標

- 依存について理解し、依存関係を操り、適切な設計・アーキテクチャを選択できるようにする

# クラスの依存関係について

## 依存とは

「クラスAがクラスBに依存する」という時、以下のことが言える。

- クラスBが変更されると、クラスAも修正スコープに入る
- クラスAはクラスBの詳細を知っている必要がある

コード上では、以下のように表現される。

```ts
class A {
  hoge() {
    const b = new B();
    // bへの処理
    return fuga
  }  
}
```

## 依存することで困ること

- Bが修正されたら、Aも修正しなければならないので、修正時のスコープが広がる
- クラスAの処理を実装するのに、クラスBのことも考えなければならない
- Bを拡張できない

### 例1-1: キーボードに入力し、それをプリンタに出力するプログラム

```ts
class Copy {
  execute() {
    let input;
    while ((input = ReadKeyBoard.read()) !== EOF) {
      WritePrinter.write(input);
    }
  }
}
```

これはこう書いても同じこと。

```ts
class Copy {
  execute() {
    let input;
    const readKeyboard = new ReadKeyboad();

    while ((input = readKeyboard.read()) !== EOF) {
      const writePrinter = new WritePrinter();
      writerPrinter.write(input);
    }
  }
}
```

### 例1-2: もしこのプログラムを、プリンタではなくディスクに書き込むようにしたければ？

```ts
class Copy {
  costructor(
    protected device: Device
  ) {}

  execute() {
    let input;
    const readKeyboard = new ReadKeyboad();

    while ((input = readKeyboard.read()) !== EOF) {
      if (device === 'Printer') {
        const writePrinter = new WritePrinter();
        writerPrinter.write(input);
      } else {
        const writeDisk = new WriteDisk();
        writerDisk.write(input);
      }
    }
  }
}
```

- さらに、このプログラムを、ディスクでなく、CloudStorageに書き込むようにしたければ？…
- 変更があるたびに、if文を追加していく？

-> Copyクラスが、Writerの詳細を知っている状態になっている。Copyはただ、「入力を読んで、出力先に書き込む」だけでいいはずなのに、デバイスが何であるかによる処理わけまでここでしている。

## 依存の注入（Dependency Injection）

処理の詳細に依存関係を記述しないことで、クラス間を疎結合にしていくべき。


## レイヤーを分ける



## 抽象に依存させる


## 参考

http://techdiary.hateblo.jp/entry/2017/11/24/022040
https://www.labri.fr/perso/clement/enseignements/ao/DIP.pdf