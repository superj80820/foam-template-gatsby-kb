# 喜歡解決問題的髒桶子

- QA

    - robot framework
    - selenium

- 管理

    - 面試

- backend

    - 壓測

        - [[k6]]

    - containerized

        - k8s
        - event source
        - Grofana
        - Elastecsearch
        - service mesh

            - istio
            - linkerd

        - docker

    - cicd

        - jenkins

    - javascript
    - python
    - golang

        - goroutine
        - lock

    - db

        - lock
        - index
        - partition
        - 分表分庫

    - message queue

        - kafka
        - rabbitMQ
        - redis

    - concurrency

        - cache

            - redis
                - 反向索引

        - lock

            - 樂觀鎖

                - 互斥鎖

                    - 死鎖
                    - 活鎖

            - 悲觀鎖
            - 分散式鎖

    - design pattern

        - [[13-UML-class-diagrams]]
        - Concurrency 併發模式: 如何讓程式高併發，並足夠安全，不產生 race condition、dead lock 等問題

            - [[02-single-threaded-execution-pattern]]
            - [[03-read-write-lock-pattern]]
            - [[04-guarded-suspension-pattern]]
            - [[05-thread-per-message-pattern]]
            - [[06-feature-pattern]]
            - [[07-fan-out-fan-inpattern]]
            - [[08-producer-consumer-pattern]]
            - [[09-worker-pool-pattern]]
            - [[10-two-phase-termination-pattern]]
            - [[11-thread-specific-storage-pattern]]
            - [[12-concurrency-patterns-融會貫通-with-graceful-shutdown]]

        - Creational 建立模式: 如何有效的生產與管理物件

            - [[14-simple-factory-pattern]]
            - [[15-factory-method-pattern]]
            - [[16-abstract-factory-pattern]]
            - [[17-builder-pattern]]
            - [[18-singleton-pattern]]
            - [[19-prototype-pattern]]

        - Structural 結構模式: 如何設計出低耦合的物件關係

            - [[20-adapter-pattern]]
            - [[21-bridge-pattern]]
            - [[22-decorator-pattern]]
            - [[23-facade-pattern]]
            - [[24-composite-pattern]]
            - [[25-flyweight-pattern]]
            - [[26-proxy-pattern]]

        - Behavioral 行為模式: 如何讓物件互動的更彈性、有效率，職責更清晰

            - [[27-chain-of-responsibility]]
            - [[28-command-pattern]]
            - [[29-iterator-pattern]]
            - [[30-strategy-pattern]]

- 交易所

    - 配息, 除息交易日
    - [[止盈, 止損]], 做空, 做多
    - 融資：投資人向券商借錢買股票
    - 多頭（牛市）, 空頭（熊市）
    - 盤整
    - 回
    - 平台

        - [[bito]]

    - 掛買賣單

        - post only
        - OCO
        - 限價停損
        - [[全部成交、部分成交]]
        - [[撮合]]
        - [[交割]]

- 區塊鏈

    - 隨機性

	    - [[self-cards/整理/vrf]]
	    - [[chainlink]]

    - 交易協定

        - utxo
        - account base

    - 幣種

        - solana
        - eth
        - ada
        - btc

- 雜談

    - [[01-evangelion-終-心得]]
