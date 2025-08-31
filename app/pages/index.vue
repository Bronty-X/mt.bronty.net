<script setup lang="ts">
import { UBadge, UButton } from '#components';

</script>

<template>
    <div >
        <div class="w-[80%] mx-auto py-24 flex items-center border-slate-300">
            <h1 class=" text-4xl font-medium">
                教材一覧<br>
                <span class="text-lg font-light">materials</span>
            </h1>
        </div>
        
        <table class="table-auto w-[80%] mx-auto mt-4 border-collapse border-slate-400">
            <tbody>
                <tr class=" border-b border-slate-300">
                    <td>Unityで作るゴルフゲーム</td>
                    <td>2024/06/15</td>
                    <td>ver1.0</td>
                    <td><UButton to="https://cnt.alphamirai.jp/GolfAsset1.0.0.unitypackage" icon="ic:baseline-download" color="neutral" size="sm" >ダウンロード</UButton></td>
                </tr>
            </tbody>

        </table>
    </div>
</template>