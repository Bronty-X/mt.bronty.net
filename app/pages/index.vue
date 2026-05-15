

<template>
    <div class=" min-h-screen">
        <div class="w-[80%] mx-auto py-24 my-5 flex items-center border-slate-300 bg-[url('/UnityMatrialImage.png')] bg-right bg-no-repeat rounded-2xl">
            <h1 class=" text-4xl font-medium">
                教材一覧<br>
                <span class="text-lg font-light">materials</span>
            </h1>
        </div>
        
        <table class="table-auto w-[80%] mx-auto my-8 border-collapse border-slate-400">
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
        },
        {
            title:'Unityでつくるパチンコゲーム',
            updated: '2025/11/21',
            version: 'ver1.0',
            downloadLink: 'https://obj.bronty.net/Pachinko1.0.0.unitypackage'
        },
        {
            title:'Unityでつくるエアホッケー',
            updated: '2026/01/17',
            version: 'ver1.0',
            downloadLink: 'https://obj.bronty.net/airhockey/GameManager.cs'
        },
        {
            title:'Unityでつくるエアホッケー2',
            updated: '2026/02/07',
            version: 'ver1.0',
            downloadLink: 'https://obj.bronty.net/airhockey/AirHockey%E3%81%AE%E3%82%B3%E3%83%92%E3%82%9A%E3%83%BC.zip'
        },
        {
            title:"Unityでつくるエアホッケー3",
            updated:"2025/03/07",
            version:"ver1.0",
            downloadLink:"https://obj.bronty.net/airhockey/AirHockeyV3.unitypackage"
        },
        {
            title:"Unityで円周率を計算してみよう",
            updated:"2026/03/22",
            version:"ver1.0",
            downloadLink:"https://obj.bronty.net/UnityPi.unitypackage"
        },
        {
            title:"Google Colaboratoryを使って円周率を計算してみよう!",
            uupdated:"2026/04/18",
            version:"ver1.0",
            downloadLink:"https://colab.research.google.com/drive/18N24PgCxPj8xSaHhT2CNGg0WB-NgdWUH?usp=sharing"
        },
        {
            title:"Unityでゴルフを作ろ改良版",
            updated:"2026/05/15",
            version:"ver1.0",
            downloadLink:"https://obj.bronty.net/golf1.0.2.unitypackage"

        }
      ]
    }
  }
}

</script>
