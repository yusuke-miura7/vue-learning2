<template>
    <div>
        <slot name="title"></slot>
    </div>
    <div>
        <slot name="content"></slot>
    </div>
    <div>
        <slot name="actions"></slot>
    </div>
    <div>
        <slot name="scoped" message="ユーザ"></slot>
        <slot message="複数のpropsの設定" content="コンテスト"></slot>
        
    </div>

</template>