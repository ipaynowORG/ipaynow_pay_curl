## 聚合支付CURL方式使用举例 ##

### 查看是否支持https ###
	
	curl -V

如下表示已经支持https(SSL support)

    curl 7.19.7 (x86_64-redhat-linux-gnu) libcurl/7.19.7 NSS/3.27.1 zlib/1.2.3 libidn/1.18 libssh2/1.4.2
    Protocols: tftp ftp telnet dict ldap ldaps http file https ftps scp sftp 
    Features: GSS-Negotiate IDN IPv6 Largefile NTLM SSL libz 

	

### 举例 ###

报文格式及相关签名算法等详见API文档。
举例如下


-- 微信被扫

	curl --tlsv1.1 -d "mhtCharset=UTF-8&payChannelType=13&mhtLimitPay=0&appId=150753082825470&mhtSignType=MD5&mhtOrderStartTime=20171106160457&mhtOrderNo=0rQi6rtXKM1dH&mhtOrderDetail=%E6%B5%8B%E8%AF%95%E5%95%86%E5%93%81%E6%8F%8F%E8%BF%B0%21%40%23&mhtSignature=eb5056ad8253c01ab52984123de2d4e1&funcode=WP001&mhtOrderAmt=1&version=1.0.0&mhtOrderTimeOut=2000&channelAuthCode=135561256524707048&mhtOrderName=%E6%B5%8B%E8%AF%95%E5%95%86%E5%93%81%21%40%23&deviceType=05&mhtOrderType=01&notifyUrl=https%3A%2F%2Fop-tester.ipaynow.cn%2Fpaytest%2Fnotify&mhtCurrencyType=156&appKey=8jTST7ywIBY0QQ3RlcxWEl08Xj9gaYyQ" "https://pay.ipaynow.cn/"

	responseCode=A001&appId=150753082825470&mhtOrderNo=0rQi6rtXKM1dH&signType=MD5&funcode=WP001&payTime=20171106160515&mhtOrderAmt=1&transStatus=A001&version=1.0.0&channelOrderNo=4200000032201711062858238383&payConsumerId=oeMyBjlVC2s9swo3vyAw_lFG4Dxw&nowPayOrderNo=200701201711061605130892526&responseMsg=E000%23%E6%88%90%E5%8A%9F%5B%E6%88%90%E5%8A%9F%5D&discountAmt=0&oriMhtOrderAmt=1&signature=f551fbafd09c207a752822bd9028d329&responseTime=20171106160515


-- 微信主扫

	curl --tlsv1.1 -d "mhtCharset=UTF-8&payChannelType=13&mhtLimitPay=0&appId=150753086263684&mhtSignType=MD5&mhtOrderStartTime=20171106161009&mhtOrderNo=no2ygeNG9TXRU&mhtOrderDetail=%E6%B5%8B%E8%AF%95%E5%95%86%E5%93%81%E6%8F%8F%E8%BF%B0%21%40%23&mhtSignature=5198bcd94113b8efd0002ee3b14add0a&funcode=WP001&mhtOrderAmt=1&version=1.0.0&mhtOrderTimeOut=2000&mhtOrderName=%E6%B5%8B%E8%AF%95%E5%95%86%E5%93%81%21%40%23&deviceType=08&mhtOrderType=01&outputType=0&notifyUrl=https%3A%2F%2Fop-tester.ipaynow.cn%2Fpaytest%2Fnotify&mhtCurrencyType=156&appKey=zHGKLmQaU9PLMEGObyubsV5uhDAeYVqQ" "https://pay.ipaynow.cn/"
	
	responseCode=A001&tn=data%3Aimage%2Fpng%3Bbase64%2CiVBORw0KGgoAAAANSUhEUgAAASwAAAEsCAIAAAD2HxkiAAAFqUlEQVR42u3aQZKDMBAEQf7%2Fae8bHOuhe6SsM2ELMclFPB9J0R5bIEEoQSgJQglCSRBKEEqCUIJQEoQShJIglCCUBKEEoSQIJQglQShBKAlCCUJJEEoQSoJQglAShBKEkiCUIJQEoQShJAglCCWtQPgsafp%2Bt%2Fz%2B9P%2FeNg8QQgghhBBCCCGEEEIIIYQQQgghhBBCCCGEEEIIIYQQJm7y%2FWG6bd%2B%2BXeep8wAhhBBCCCGEEEIIIYQQQgghhBBCCCGEEEIIIYQQQgjh%2F25y%2BrA1NTRb0Lats20eIIQQQgghhBBCCCGEEEIIIYQQQgghhBBCCCGEEEIIIbx706d%2FJzUcW16CEEIIIYQQQgghhBBCCCGEEEIIIYQQQgghhBBCCCGEEEII4Tyq1L5BCCGEEEIIIYQQQgghhBBCCCGEEEIIIYQQQgghhBBCeAfC7etJDU1b5gFCCCGEEEIIzQOEEEIIIYQQQgghhBBCCCGEEEIIIYQQ3jQ0rj%2F7JQIhhBBCCKHrIYQQQgghhND1EEIIIYQQQuh6CCGEEEII7%2BhXD2n6YbdhE4QQQgghhBAKQgghhBBCCAUhhBBCCCGEghBCCO9GmDpM33KYO4287SOHLfsJIYQQQgghhBBCCCGEEEIIIYQQQgghhBBCCCGEEEII4cvLCh0ipw6724a%2B7b7a7hdCCCGEEEIIIYQQQgghhBBCCCGEEEIIIYQQQgghhBDCnZvVNhxbXjpbXrJtH2NACCGEEEIIIYQQQgghhBBCCCGEEEIIIYQQQgghhBDeijCFIbXO1NBsH9a25w4hhBBCCCGEEEIIIYQQQgghhBBCCCGEEEIIIYQQQgjhWdjahju1%2FlPXAyGEEEIIIYQQQgghhBBCCCGEEEIIIYQQQgghhBBCCGEHwi14vv3fUxH%2B6n5%2Fdf3Z%2BCGEEEIIIYQQQgghhBBCCCGEEEIIIYQQQgghhBBCCO9DuAXJFvwpJNNDvOV5QQghhBBCCCGEEEIIIYQQQgghhBBCCCGEEEIIIYQQQtiNZwuG1LBuWf%2FniCCEEEIIIYQQQgghhBBCCCGEEEIIIYQQQgghhBBCCM9F2La5bYfXtw13aj1XH9ZDCCGEEEIIIYQQQgghhBBCCCGEEEIIIYQQQgghhBAGEE5visP07P%2Bm7mvLeiCEEEIIIYQQQgghhBBCCCGEEEIIIYQQQgghhBBCCB3Wv%2FtQU8itJ%2FsynV4nhBBCCCGEEEIIIYQQQgghhBBCCCGEEEIIIYQQQgghhN2H9bcddrcN%2FZaPKyCEEEIIIYQQQgghhBBCCCGEEEIIIYQQQgghhBBCCCHs2PRnSacO3%2FZSL2sIIYQQQgghhBBCCCGEEEIIIYQQQgghhBBCCCGEEEIIz6rtcHx6aFL31faxBIQQQgihIIQQQgghhFAQQgghhBBCKAghhBBCCCHs2MS2Q97UvrX9zvR%2Btq0fQgghhBBCCCGEEEIIIYQQQgghhBBCCCGEEEIIIYQQwneHILWeUzFvua9pPBBCCCGEEEIIIYQQQgghhBBCCCGEEEIIIYQQQgghhBDuHPq2w%2BItQ9yGPHWYDiGEEEIIIYQQQgghhBBCCCGEEEIIIYQQQgghhBBCCCGEiX2Yvq%2B2jyW2zw%2BEEEIIIYQQQgghhBBCCCGEEEIIIYQQQgghhBBCCCGEdyBsQ3IqzhQeCCGEEEIIIYQQQgghhBBCCCGEEEIIIYQQQgghhBBCCDsQbn8pbB%2B%2B6abXuWUOIYQQQgghhBBCCCGEEEIIIYQQQgghhBBCCCGEEEIIb0XYVmr9qZfalpdRag4hhBBCCCGEEEIIIYQQQgghhBBCCCGEEEIIIYQQQgghlAShBKEkCCUIJUEoQSgJQglCSRBKEEqCUIJQEoQShJIglCCUBKEEoSQIJQglQShBKAlCCUJJEEoQSoJQglAShBKEkiCUIJQEoVTZHwPA%2F%2BqLfh6uAAAAAElFTkSuQmCC&appId=150753086263684&mhtOrderNo=no2ygeNG9TXRU&signType=MD5&nowPayOrderNo=200301201711061610101147392&responseMsg=E000%23%E6%88%90%E5%8A%9F%5B%E6%88%90%E5%8A%9F%5D&funcode=WP001&signature=f14b46f662822cfe21bfc5139805bf8e&responseTime=20171106161010&version=1.0.0


-- 微信公众号

	curl --tlsv1.1 -d "mhtCharset=UTF-8&payChannelType=13&mhtLimitPay=0&appId=150753094138037&mhtSignType=MD5&mhtOrderStartTime=20171106161831&mhtOrderNo=dM6eXH5MRivZi&mhtOrderDetail=%E6%B5%8B%E8%AF%95%E5%95%86%E5%93%81%E6%8F%8F%E8%BF%B0%21%40%23&mhtSignature=451128fb92128b3ba221e9ceb67e20de&frontNotifyUrl=http%3A%2F%2Fwww.baidu.com&funcode=WP001&mhtOrderAmt=1&version=1.0.0&mhtOrderTimeOut=2000&mhtOrderName=%E6%B5%8B%E8%AF%95%E5%95%86%E5%93%81%21%40%23&deviceType=0600&mhtOrderType=01&outputType=0&notifyUrl=https%3A%2F%2Fop-tester.ipaynow.cn%2Fpaytest%2Fnotify&mhtCurrencyType=156&appKey=n0bloMQxHYDfwnqlF6poU6P6i9mXzdWB

	https://open.weixin.qq.com/connect/oauth2/authorize?appid=wx99df53752bdf6df2&redirect_uri=https%3A%2F%2Fpay.ipaynow.cn%2FpaymentGateway%2F%3FtransId%3D200406201711061618317650283%26appId%3D150753094138037%26mhtLimitPay%3D0%26deviceType%3D0600%26channelType%3D13%26version%3D1.0.0%26remoteIp%3D60.253.242.122&response_type=code&scope=snsapi_base#wechat_redirect


-- 微信H5

	curl --tlsv1.1 -d "mhtCharset=UTF-8&payChannelType=13&mhtLimitPay=0&appId=1482402994841173&mhtSignType=MD5&mhtOrderStartTime=20171106161905&mhtOrderNo=LsX6KSQrriXBJ&mhtOrderDetail=%E6%B5%8B%E8%AF%95%E5%95%86%E5%93%81%E6%8F%8F%E8%BF%B0%21%40%23&consumerCreateIp=60.253.242.122&mhtSignature=d4e18e20c6cd49f47402fb496e1352a1&frontNotifyUrl=http%3A%2F%2Fwww.baidu.com&funcode=WP001&mhtOrderAmt=1&version=1.0.0&mhtOrderTimeOut=2000&mhtOrderName=%E6%B5%8B%E8%AF%95%E5%95%86%E5%93%81%21%40%23&deviceType=0601&mhtOrderType=01&outputType=1&notifyUrl=https%3A%2F%2Fop-tester.ipaynow.cn%2Fpaytest%2Fnotify&mhtCurrencyType=156&appKey=zy1gE5oiWRvUYh0fUVDsAbCeLVpUl24V" "https://pay.ipaynow.cn/"

	responseCode=A001&tn=https%3A%2F%2Fpay.ipaynow.cn%2Fwxpay%3FnowPayOrderNo%3D200601201711061619065806599%26deviceType%3D0601%26version%3D1.0.0%26url%3Dhttps%253A%252F%252Fwx.tenpay.com%252Fcgi-bin%252Fmmpayweb-bin%252Fcheckmweb%253Fprepay_id%253Dwx201711061619067f25a411970813030834%2526package%253D467013382&appId=1482402994841173&mhtOrderNo=LsX6KSQrriXBJ&signType=MD5&nowPayOrderNo=200601201711061619065806599&responseMsg=E000%23%E6%88%90%E5%8A%9F%5B%E6%88%90%E5%8A%9F%5D&funcode=WP001&signature=7d165971c3bfafa7dc219d80bd4453ca&responseTime=20171106161906&version=1.0.0



-- 支付宝被扫

	curl --tlsv1.1 -d "mhtCharset=UTF-8&payChannelType=12&mhtLimitPay=0&appId=1482402994841173&mhtSignType=MD5&mhtOrderStartTime=20171106162248&mhtOrderNo=HQhbkgDd5lyUl&mhtOrderDetail=%E6%B5%8B%E8%AF%95%E5%95%86%E5%93%81%E6%8F%8F%E8%BF%B0%21%40%23&mhtSignature=ea39c2625b46cee5ea1ab359989a4395&funcode=WP001&mhtOrderAmt=1&version=1.0.0&mhtOrderTimeOut=2000&channelAuthCode=281038179378625252&mhtOrderName=%E6%B5%8B%E8%AF%95%E5%95%86%E5%93%81%21%40%23&deviceType=05&mhtOrderType=01&notifyUrl=https%3A%2F%2Fop-tester.ipaynow.cn%2Fpaytest%2Fnotify&mhtCurrencyType=156&appKey=zy1gE5oiWRvUYh0fUVDsAbCeLVpUl24V" "https://pay.ipaynow.cn/"

	responseCode=A002&appId=1482402994841173&mhtOrderNo=HQhbkgDd5lyUl&signType=MD5&funcode=WP001&responseMsg=E002%23%E8%AE%A2%E5%8D%95%E5%88%9D%E5%A7%8B%E5%8C%96-%E6%94%AF%E4%BB%98%E9%80%9A%E9%81%93%E9%94%99%E8%AF%AF%5B%E5%95%86%E6%88%B7%E5%BA%94%E7%94%A8%E4%BF%A1%E6%81%AF%E6%9C%AA%E9%85%8D%E7%BD%AE%E6%88%96%E4%B8%8D%E5%90%88%E6%B3%95%5D&signature=7cd24fab531baf8cde96befc173e3f93&responseTime=20171106162249&version=1.0.0


-- 支付宝主扫

	curl --tlsv1.1 -d "mhtCharset=UTF-8&payChannelType=12&mhtLimitPay=0&appId=150753086263684&mhtSignType=MD5&mhtOrderStartTime=20171106162402&mhtOrderNo=EefKRASXoTQW3&mhtOrderDetail=%E6%B5%8B%E8%AF%95%E5%95%86%E5%93%81%E6%8F%8F%E8%BF%B0%21%40%23&mhtSignature=3620802b6fc1fcb8e82f01da60610100&funcode=WP001&mhtOrderAmt=1&version=1.0.0&mhtOrderTimeOut=2000&mhtOrderName=%E6%B5%8B%E8%AF%95%E5%95%86%E5%93%81%21%40%23&deviceType=08&mhtOrderType=01&outputType=0&notifyUrl=https%3A%2F%2Fop-tester.ipaynow.cn%2Fpaytest%2Fnotify&mhtCurrencyType=156&appKey=zHGKLmQaU9PLMEGObyubsV5uhDAeYVqQ" "https://pay.ipaynow.cn/"

	responseCode=A001&tn=data%3Aimage%2Fpng%3Bbase64%2CiVBORw0KGgoAAAANSUhEUgAAASwAAAEsCAIAAAD2HxkiAAAFrElEQVR42u3dQW6FMBBEQe5%2F6eQMiTDTPa63Rj9gprwxUp4fSaM9lkCCUIJQEoQShJIglCCUBKEEoSQIJQglQShBKAlCCUJJEEoQSoJQglAShBKEkiCUIJQEoQShJAglCCVBKEEoCUIJQkkQShBKqkD4lJS2Dn%2F9nan7MQ8QQgghhBYdQvMAIYQQQmjRITQPEEIIIYQWHULzACGEEEJ4cmjS7uf0S235%2FalNZMd8QgghhBBCCCGEEEIIIYQQQgghhBBCCCGEEEIIIYQQQvjf4bhtCKauT0O7Yx4ghBBCCCGEEEIIIYQQQgghhBBCCCGEEEIIIYQQQgghbBuC0%2BvTsm4QQgghhBBCCCGEEEIIIYQQQgghhBBCCCGEEEIIIYQQQuiw%2BIn716tpzwshhBBCCCGEEEIIIYQQQgghhBBCCCGEEEIIIYQQQgghhA1Defrvtn%2Bc0DX0EEIIoXmAEEIIIYQQQvMAIYQQQgghhBBCCCGEEEIIIYTTCNPaOsQt17fMA4QQQgghhK6HEEIIIYQQQtdDCCGEEEIIoeshhBBCCCHUG0O29XlNAoQQQgghhBAKQgghhBBCCAUhhBBCCCGEghBCCO9GODWUWw%2Fx31q30%2FdvU4MQQgghhBBCCCGEEEIIIYQQQgghhBBCCCGEEEIIIbwb4W2YpzaLtE1kap270EIIIYQQQgghhBBCCCGEEEIIIYQQQgghhBBCCCGEEO5FmDY0acO9dZ1Pv5efFUEIIYQQQgghhBBCCCGEEEIIIYQQQgghhBBCCCGEEEL4FZK04Ug7jE5DshsnhBBCCCGEEEIIIYQQQgghhBBCCCGEEEIIIYQQQgjhXoSnFxeeb%2B6zfR3eun8IIYQQQgghhBBCCCGEEEIIIYQQQgghhBBCCCGEEEIIv33ItMPZtKFJO8Tfev8QQgghhBBCCCGEEEIIIYQQQgghhBBCCCGEEEIIIYQQfjs0LbWsw1ubC1QQQgghhBBCCCGEEEIIIYQQQgghhBBCCCGEEEIIIYQQTqBNO5SfGr40VGk4Mz8CgRBCCCGEEEIIIYQQQgghhBBCCCGEEEIIIYQQQgghvA9h2jC1DOXUc9msIYQQQgghhBBCCCGEEEIIIYQQQgghhBBCCCGEEEIIITy5WFOLu%2FVjgNOH4FObRdr6QAghhBBCCCGEEEIIIYQQQgghhBBCCCGEEEIIIYQQQpi9KO3D0bJuaTjTNl8IIYQQQgghhBBCCCGEEEIIIYQQQgghhBBCCCGEEMJbEbZgbh%2Bmlt%2FPRAIhhBBCCCGEEEIIIYQQQgghhBBCCCGEEEIIIYQQQghh6iKePjRPey5981EEhBBCCCGEEEIIIYSCEEIIIYQQQkEIIYQQQgihILy7tOFIG6a0zchhPYQQQgghhBBCCCGEEEIIIYQQQgghhBBCCCGEEEIIYQbC2w5%2Fp4b49O9MfeTQdfgOIYQQQgghhBBCCCGEEEIIIYQQQgghhBBCCCGEEEII4VeHuafvZyvaqfVpf14IIYQQQgghhBBCCCGEEEIIIYQQQgghhBBCCCGEEEIIv32pU4fFaTinkLd%2FdJEZhBBCCCGEEEIIIYQQQgghhBBCCCGEEEIIIYQQQgghhFsQtiCZeo8tmxqEEEIIIYQQQgghhBBCCCGEEEIIIYQQQgghhBBCCCGEEE4MQcswOdyHEEIIIYQQQgghhBBCCCGEEEIIIYQQQgghhBBCCCGEMO8w9PtD5PZNKm3zatmUIYQQQgghhBBCCCGEEEIIIYQQQgghhBBCCCGEEEIIIcxY9KmXNDX0Ww%2B7dxzKQwghhBBCCCGEEEIIIYQQQgghhBBCCCGEEEIIIYQQ3odQEoQShJIglCCUBKEEoSQIJQglQShBKAlCCUJJEEoQShBKglCCUBKEEoSSIJQglAShBKEkCCUIJUEoQSgJQglCSRBKEEqCUIJQ0qF%2BAf4%2Bx7LhOjnTAAAAAElFTkSuQmCC&appId=150753086263684&mhtOrderNo=EefKRASXoTQW3&signType=MD5&nowPayOrderNo=200301201711061624031147536&responseMsg=E000%23%E6%88%90%E5%8A%9F%5B%E6%88%90%E5%8A%9F%5D&funcode=WP001&signature=02ba343e9104b72fbd830e78c2420276&responseTime=20171106162403&version=1.0.0


-- 支付宝公众号

	curl --tlsv1.1 -d "mhtCharset=UTF-8&payChannelType=12&mhtLimitPay=0&appId=150753094138037&mhtSignType=MD5&mhtOrderStartTime=20171106162449&mhtOrderNo=leafsHwxKIZYv&mhtOrderDetail=%E6%B5%8B%E8%AF%95%E5%95%86%E5%93%81%E6%8F%8F%E8%BF%B0%21%40%23&mhtSignature=be43d0e5c72c8390d17dc122c0051fef&frontNotifyUrl=http%3A%2F%2Fwww.baidu.com&funcode=WP001&mhtOrderAmt=1&version=1.0.0&mhtOrderTimeOut=2000&mhtOrderName=%E6%B5%8B%E8%AF%95%E5%95%86%E5%93%81%21%40%23&deviceType=0600&mhtOrderType=01&outputType=0&notifyUrl=https%3A%2F%2Fop-tester.ipaynow.cn%2Fpaytest%2Fnotify&mhtCurrencyType=156&appKey=n0bloMQxHYDfwnqlF6poU6P6i9mXzdWB" "https://pay.ipaynow.cn/"

	https://openauth.alipay.com/oauth2/publicAppAuthorize.htm?app_id=2016090701864626&scope=auth_base&redirect_uri=https%3A%2F%2Fpay.ipaynow.cn%2FgetAuthCode%3FtransId%3D200402201711061624507660168%26version%3D1.0.0&state=106_38193752_0070340501


-- 支付宝h5

	curl --tlsv1.1 -d "mhtCharset=UTF-8&payChannelType=12&mhtLimitPay=0&appId=1482402994841173&mhtSignType=MD5&mhtOrderStartTime=20171106162557&mhtOrderNo=mH32DQfWJ5Uer&mhtOrderDetail=%E6%B5%8B%E8%AF%95%E5%95%86%E5%93%81%E6%8F%8F%E8%BF%B0%21%40%23&mhtSignature=3378778c6248407f93e27e648e388148&frontNotifyUrl=http%3A%2F%2Fwww.baidu.com&funcode=WP001&mhtOrderAmt=1&version=1.0.0&mhtOrderTimeOut=2000&mhtOrderName=%E6%B5%8B%E8%AF%95%E5%95%86%E5%93%81%21%40%23&deviceType=0601&mhtOrderType=01&outputType=1&notifyUrl=https%3A%2F%2Fop-tester.ipaynow.cn%2Fpaytest%2Fnotify&mhtCurrencyType=156&appKey=zy1gE5oiWRvUYh0fUVDsAbCeLVpUl24V" "https://pay.ipaynow.cn/"

	responseCode=A001&tn=https%3A%2F%2Fopenapi.alipay.com%2Fgateway.do%3Falipay_sdk%3Dalipay-sdk-java-dynamicVersionNo%26app_auth_token%3D201710BB531e0f56e1f54a799edae5c3a714bA10%26app_id%3D2016090701862812%26biz_content%3D%257B%2522total_amount%2522%253A%25220.01%2522%252C%2522timeout_express%2522%253A%252233m%2522%252C%2522product_code%2522%253A%2522QUICK_WAP_PAY%2522%252C%2522subject%2522%253A%2522%25E6%25B5%258B%25E8%25AF%2595%25E5%2595%2586%25E5%2593%2581%2521%2540%2523%2522%252C%2522out_trade_no%2522%253A%2522200601201711061625585809761%2522%252C%2522extend_params%2522%253A%2522%257B%255C%2522sys_service_provider_id%255C%2522%253A%255C%25222088421452327167%255C%2522%257D%2522%257D%26charset%3DUTF-8%26format%3Djson%26method%3Dalipay.trade.wap.pay%26notify_url%3Dhttps%253A%252F%252Fpay.ipaynow.cn%252FaliPayNotifyNew%252F2006%252F0A4735ae9a516fe3B070_22_00314490241b1aced974fe5015B1123_116_71892481%26return_url%3Dhttps%253A%252F%252Fpay.ipaynow.cn%252FalipayFrontNotifyNew%252F1.0.0%252F2006%252F0A4735ae9a516fe3B070_22_00314490241b1aced974fe5015B1123_116_71892481%26sign%3DKyoX6rQ6CEP0BL61D2Bh6Q6sAY%252BdpOTglvfT7Pk9Wnbt8vOM7HJwtMDo6lX2dNJp%252BBljy7zk%252Brm6JjuHUg42ajcjGIGC%252BA4AnN9Q5ZutB4CJQcndvgU97akmyBbh1%252BA9Y7Aey7h%252BYsSChhrQE6PkSYxZf7C8oGMu0MOlfKkZD6w%253D%26sign_type%3DRSA%26timestamp%3D2017-11-06%2B16%253A25%253A58%26version%3D1.0%26sign%3DKyoX6rQ6CEP0BL61D2Bh6Q6sAY%252BdpOTglvfT7Pk9Wnbt8vOM7HJwtMDo6lX2dNJp%252BBljy7zk%252Brm6JjuHUg42ajcjGIGC%252BA4AnN9Q5ZutB4CJQcndvgU97akmyBbh1%252BA9Y7Aey7h%252BYsSChhrQE6PkSYxZf7C8oGMu0MOlfKkZD6w%253D&appId=1482402994841173&mhtOrderNo=mH32DQfWJ5Uer&signType=MD5&nowPayOrderNo=200601201711061625585809761&responseMsg=E000%23%E6%88%90%E5%8A%9F%5B%E6%88%90%E5%8A%9F%5D&funcode=WP001&signature=d538890b596821d391837765f52b3c7a&responseTime=20171106162558&version=1.0.0


-- 支付宝网页web

	curl --tlsv1.1 -d "mhtCharset=UTF-8&payChannelType=12&mhtLimitPay=0&appId=150753107733024&mhtSignType=MD5&mhtOrderStartTime=20171106162646&mhtOrderNo=Pe1uv0NhbbJAe&mhtOrderDetail=%E6%B5%8B%E8%AF%95%E5%95%86%E5%93%81%E6%8F%8F%E8%BF%B0%21%40%23&mhtSignature=ddff37f994b17695c0c8e045cd7b3b75&funcode=WP001&mhtOrderAmt=1&version=1.0.0&mhtOrderTimeOut=2000&mhtOrderName=%E6%B5%8B%E8%AF%95%E5%95%86%E5%93%81%21%40%23&deviceType=04&mhtOrderType=01&outputType=0&notifyUrl=https%3A%2F%2Fop-tester.ipaynow.cn%2Fpaytest%2Fnotify&mhtCurrencyType=156&appKey=4Bl0qsRhe5xhRn3sO0Kwomqts6WgpMbq" "https://pay.ipaynow.cn/"

	responseCode=A001&tn=https%3A%2F%2Fopenapi.alipay.com%2Fgateway.do%3Falipay_sdk%3Dalipay-sdk-java-dynamicVersionNo%26app_id%3D2017020805568925%26biz_content%3D%257B%2522subject%2522%253A%2522%25E6%25B5%258B%25E8%25AF%2595%25E5%2595%2586%25E5%2593%2581%2521%2540%2523%2522%252C%2522out_trade_no%2522%253A%2522APU1620171106000218755%2522%252C%2522timeout_express%2522%253A%252233m%2522%252C%2522total_amount%2522%253A%25220.01%2522%252C%2522product_code%2522%253A%2522FAST_INSTANT_TRADE_PAY%2522%252C%2522sub_merchant%2522%253A%257B%2522merchant_id%2522%253A%25222088721021356849%2522%257D%257D%26charset%3DUTF-8%26format%3Djson%26method%3Dalipay.trade.page.pay%26notify_url%3Dhttp%253A%252F%252Fwx.mposbank.com%252Ftdcctp%252Fnotify%252Fpc_notify.tran%26return_url%3Dhttp%253A%252F%252Fwx.mposbank.com%252Ftdcctp%252Freturn%252Fpc_return.tran%26sign%3DKz2X9uI0IjQ%252FatoZVBtdQbDtKmBpM1dXlKDFEH3gM7qwYSXapvWrmghsr%252BzCTWFInkhUgcRV%252B%252BcyufCrB2Uqo2Uq6%252FnlLxia%252BeVBhmGZvI8wCmKC6ez0GWKgdwdTD7j6Df1aR3qoP%252FlFrJX4AW%252FwMvyjLF1t7SRdxQghI9H%252BE7E%253D%26sign_type%3DRSA%26timestamp%3D2017-11-06%2B16%253A26%253A47&appId=150753107733024&mhtOrderNo=Pe1uv0NhbbJAe&signType=MD5&nowPayOrderNo=202101201711061626472177677&responseMsg=E000%23%E6%88%90%E5%8A%9F%5B%E6%88%90%E5%8A%9F%5D&funcode=WP001&signature=205ea000325531ae5fd3ab563bf2bab7&responseTime=20171106162647&transStatus=A004&version=1.0.0






-- 订单查询

	curl --tlsv1.1 -d "mhtCharset=UTF-8&appId=150753082825470&mhtSignType=MD5&mhtOrderNo=0rQi6rtXKM1dH&deviceType=05&mhtSignature=54dea3e699f238033973187dd75740d0&funcode=MQ002&version=1.0.0" "https://pay.ipaynow.cn/"

	appId=150753082825470&signType=MD5&payTime=20171106160514&transStatus=A001&version=1.0.0&mhtOrderTimeOut=2000&mhtOrderName=%E6%B5%8B%E8%AF%95%E5%95%86%E5%93%81%21%40%23&deviceType=05&mhtOrderType=01&nowPayOrderNo=200701201711061605130892526&responseMsg=E000%23%E6%88%90%E5%8A%9F%5B%E6%88%90%E5%8A%9F%5D&discountAmt=0&signature=9413d1483fece24e0e6cd160a8e351f7&responseTime=20171106164618&mhtCharset=UTF-8&responseCode=A001&payChannelType=13&mhtOrderStartTime=20171106160457&mhtOrderNo=0rQi6rtXKM1dH&funcode=MQ002&mhtOrderAmt=1&channelOrderNo=4200000032201711062858238383&payConsumerId=oeMyBjlVC2s9swo3vyAw_lFG4Dxw&oriMhtOrderAmt=1&mhtCurrencyType=156

-- 退款

	curl --tlsv1.1 -d "mhtCharset=UTF-8&amount=1&appId=150753082825470&reason=somereason&mhtRefundNo=fuQrDmiHnQuO4Irh4N4s&mhtOrderNo=0rQi6rtXKM1dH&signType=MD5&mhtSignature=db8b7b199b403f6f3526e261e7d2c829&funcode=R001" "https://pay.ipaynow.cn/"

	mhtCharset=UTF-8&responseCode=R000&tradeStatus=A004&appId=150753082825470&reason=somereason&mhtOrderNo=0rQi6rtXKM1dH&signType=MD5&funcode=R001&amount=1&mhtRefundNo=fuQrDmiHnQuO4Irh4N4s&nowPayOrderNo=200801201711061648220410130&responseMsg=%E6%88%90%E5%8A%9F&signature=12880667a78f694380a2c1c36db3325f&responseTime=20171106164822





