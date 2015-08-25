# clj.qrgen

A Clojure library designed to generate QRCode wrapped java [QRGen](https://github.com/kenglxn/QRGen).

## News

* Released 0.4.0, upgrade qrgen to 0.2.0

## Usage

Dependency in leiningen:

```clojure
    [clj.qrgen "0.4.0"]
```

Use it:

```clojure
(use 'clj.qrgen)
```

Create a QRCode from a text then save as a temporary file:

```clojure
(as-file (from "hello world"))
```

Created with options:

```clojure
;; override size and image type
(from "hello world" :size [250 250] :image-type JPG)
;; supply charset hint to ZXING
(from "hello world" :charset "utf-8")
;; supply error correction level hint to ZXING
(from "hello world" :correction L)
;; supply any hint to ZXING
(from "hello world" :hint {CHARACTER_SET "utf-8"})
```

Encode contact data as vcard using defaults:

```clojure
(from (vcard "John Doe"
             :email "john.doe@example.org"
			 :address "John Doe Street 1, 5678 Doestown"
			 :title "Mister"
			 :company "John Doe Inc."
			 :phonenumber "1234"
			 :website "www.example.org"))
```

As InputStream( as ring response):

```clojure
(as-input-stream (from "hello world"))
```

As OutputStream:

```clojure
(as-output-stream (from "hello world"))
```

As byte array:

```clojure
(as-bytes (from "hello world"))
```

Suppy own file name:

```clojure
(as-file (from "hello world") "QRCode.png")
```

Work with `clojure.java.io`:

```clojure
(require '[clojure.java.io :as io])
(io/file (from "hello world"))
(io/output-stream (from "hello world"))
(io/input-stream (from "hello world"))
(io/copy (io/file (from "hello world")) a-output-stream)
```

## License

Copyright © 2014 [dennis zhuang](https://github.com/killme2008).

Distributed under the Eclipse Public License version 1.0
