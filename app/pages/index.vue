

<template>
    <div class=" min-h-screen">
        <div class="w-[80%] mx-auto py-24 my-5 flex items-center border-slate-300 bg-[url('/UnityMatrialImage.png')] bg-right bg-no-repeat rounded-2xl">
            <h1 class=" text-4xl font-medium">
                教材一覧<br>
                <span class="text-lg font-light">materials</span>
            </h1>
        </div>
        
        <table class="table-auto w-[80%] mx-auto mt-8 border-collapse border-slate-400">
            <thead>
                <tr class=" border-b border-slate-300">
                    <th class="text-left py-4">タイトル</th>
                    <th class="text-left">最終更新日</th>
                    <th class="text-left">バージョン</th>
                    <th class="text-left">ダウンロード</th>
                </tr>
            </thead>
            <tbody>
                <tr class=" border-b border-slate-300 my-2" v-for="(material, index) in materials" :key="index">
                    <td class="py-4">{{ material.title }}</td>
                    <td>{{ material.updated }}</td>
                    <td>{{ material.version }}</td>
                    <td class="py-2"><UButton :to="material.downloadLink" icon="ic:baseline-download" color="neutral" size="sm" >ダウンロード</UButton></td>
                </tr>
            </tbody>

        </table>
    </div>
</template>
<script lang="js">
export default {
  data() {
    return {
      materials: [
        {
          title: 'Unityで作るゴルフゲーム',
          updated: '2025/08/31',
          version: 'ver1.0',
          downloadLink: 'https://cnt.alphamirai.jp/GolfAsset1.0.0.unitypackage'
        },
        {
            title: 'Unityで作る玉転がしゲーム',
            updated: '2025/09/01',
            version: 'ver1.0',
            downloadLink: 'https://obj.bronty.net/maze1.0.0.unitypackage'     
        }
      ]
    }
  }
}

</script>