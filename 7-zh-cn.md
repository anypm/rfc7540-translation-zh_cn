# 错误码

错误码是32位字段，用在`RST_STREAM`和超时帧中去标识流或者连接错误的原因。

错误码共享一个代码空间。 一些错误码仅仅适用于其中的一些流或者整个连接，在其他的情况下并没有明确的意义。

错误码有如下定义：

+ **NO_ERROR(0x0)**: 相关环境不作为错误处理。 例如： 超时帧可能包含该错误码来表明连接的正常关闭。

+ **PROTOCOL_ERROR (0x1)**： 终端检测到一个不确定性质的协议错误。 这个错误码用在一个更加确切的错误码不可用的情况下。

+ **INTERNAL_ERROR (0x2)**： 终端遇到了一个意外的内部错误。

+ **FLOW_CONTROL_ERROR (0x3)**： 终端检测到对等端违背了流量控制协议。

+ **SETTINGS_TIMEOUT (0x4)**： 终端发送了一个设置帧，但是没有在指定时间内得到响应。 [参见Section 6.5.3 ("Settings Synchronization")](https://tools.ietf.org/html/rfc7540#section-6.5.3)。 

+ **STREAM_CLOSED (0x5)**： 终端在流的半封闭状态接收到了帧。

+ **FRAME_SIZE_ERROR (0x6)**： 终端接收到一个超出最大尺寸的帧。

+ **REFUSED_STREAM (0x7)**： 终端拒绝流之前执行了程序处理。 [参见Section 8.1.4](https://tools.ietf.org/html/rfc7540#section-8.1.4)。

+ **CANCEL (0x8)**: 标识这个流不再是需要的。

+ **COMPRESSION_ERROR (0x9)**： 终端无法维护报头压缩上下文的连接。

+ **CONNECT_ERROR (0xa)**： 为响应一个连接请求的而建立的连接[参见：Section 8.3](https://tools.ietf.org/html/rfc7540#section-8.3)被重置或者异常关闭。

+ **ENHANCE_YOUR_CALM (0xb)**： 终端检测到其对等端的某行为可能负荷超载。

+ **INADEQUATE_SECURITY (0xc)**： 底层传输特性不符合最低安全要求。 [参见 Section 9.2](https://tools.ietf.org/html/rfc7540#section-9.2)。

+ **HTTP_1_1_REQUIRED (0xd)**： 终端应该使用`HTTP/1.1`, 而不是`HTTP/2`。

未知或者不支持的错误码**绝不会**触发任何特殊的行为。 它们可能会被当做内部错误（INTERNAL_ERROR）来处理。