<script setup>
    const quizData = {
        question: "モンテカルロ法において、精度を上げる方法は次のうちどれ？",
        options: [
            { value: "option1", label: "サンプル数を増やす" },
            { value: "option2", label: "サンプル数を減らす" },
            { value: "option3", label: "サンプル数を一定にする" },
            { value: "option4", label: "サンプル数をランダムにする" }
        ]
    };
    
</script>
<template>
    <div class=" min-h-screen w-[80%] mx-auto max-w-[800px] flex flex-col justify-center">
        <h1 class=" text-2xl font-bold">第一問</h1>
        <p class="text-2xl mt-8">モンテカルロ法において、精度を上げる方法は次のうちどれ？</p>
        <div class="mt-12">
            <UAlert
                title="ヒント"
                description="Unityのシミュレーションでモンテカルロ法を使用する場合、サンプル数を増やすことで精度が向上します。"
                color="neutral"
                variant="outline"
            />
        </div>
        <div class=" mt-8">
            <URadioGroup color="primary" variant="card" default-value="option1" :items="quizData.options" />
        </div>
        <div class=" mt-12">
            <UButton size="xl">回答</UButton>
        </div>
        
    </div>
</template>