<script setup>
import { ref } from "vue";
import t from "@/utils/MatceTools.js";
import { useRouter, useRoute } from "vue-router";
const router = useRouter();
const route = useRoute();

const tools = ref([
    { title: "Bert-VITS 2 合成", url: "\bert-vits2" },
    { title: "敬请期待", url: "" },
]);
</script>

<template>
    <div class="main">
        <div class="greeting text-brown-lighten-1">欢迎</div>
        <div class="toolBox mt-10">
            <v-card
                height="100"
                v-ripple="{ class: 'text-white' }"
                v-for="(tool, i) in tools"
                :key="i"
                cols="auto"
                class="tool d-flex bg-brown-lighten-1 elevation-0 text-white"
                @click="router.push({ path: tool.url })"
            >
                <div class="toolIcon bg-brown-lighten-3"></div>
                <div class="toolTitle">{{ tool.title }}</div>
            </v-card>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.main {
    padding: 60px;

    .greeting {
        font-size: 30px;
        font-weight: bold;
        overflow: hidden;
        margin: -10px 0;
    }

    .toolBox {
        display: flex;
        flex-wrap: wrap;
        gap: 10px;
        overflow: hidden;

        .tool {
            width: 100%;
            max-width: 100%;
            cursor: pointer;
            padding: 14px;
            display: flex;
            align-items: center;

            &Icon {
                min-width: 10px;
                height: 100%;
                border-radius: 2px;
                margin-right: 14px;
                transition: all 0.2s ease;
            }

            &Title {
                flex: 1;
                margin-top: -2px;
                // padding-right: 14px;
                overflow: hidden;
                white-space: pre-wrap;
                display: -webkit-box;
                overflow: hidden;
                text-overflow: ellipsis; //省略号
                -webkit-line-clamp: 3; //指定保留行数
                -webkit-box-orient: vertical;
            }
        }

        .tool:hover {
            background-color: #795548 !important;

            .toolIcon {
                // height: 40px;
                min-width: 20px;
                // border-radius: 5px;
                // background-color: #fff8 !important;
            }
        }

        @media (min-width: 700px) {
            .tool {
                width: calc(calc(100% - 10px) / 2);
                padding-right: 0px;
            }
        }

        @media (min-width: 900px) {
            .tool {
                width: calc(calc(100% - 20px) / 3);
            }
        }
    }
}
</style>