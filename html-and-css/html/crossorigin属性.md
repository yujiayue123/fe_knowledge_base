## crossorigin 属性

crossorigin 属性在`<audio>、<img>、<link>、<script> 和 <video>`元素中有效，它们提供对 CORS 的支持，定义该元素如何处理跨源请求，从而实现对该元素获取数据的 CORS 请求的配置。根据元素的不同，该属性可以是一个 CORS 设置属性。

| 属性值          | 描述                                                                            |
| --------------- | ------------------------------------------------------------------------------- |
| anonymous       | 对此元素的 CORS 请求将不设置凭据标志。                                          |
| use-credentials | 对此元素的 CORS 请求将设置凭证标志；这意味着请求将提供凭据。                    |
| ""              | 设置一个空的值，如 crossorigin 或 crossorigin=""，和设置 anonymous 的效果一样。 |

- 设置了 crossorigin 就相当于开启了 cors 校验。

- 开启 cors 校验之后，跨域的 script 资源在运行出错的时候，window.onerror 可以捕获到完整的错误信息。

- crossorigin=use-credentials 可以跨域带上 cookie。
