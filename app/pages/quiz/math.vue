<script setup>

    import { gsap } from "gsap";

    const tl = gsap.timeline();

    
    
    onMounted(() => {
        tl.to(".animate", { y: -20, repeat: -1, yoyo: true, ease: "power1.inOut", duration: 1 });
        gsap.to(".animate", {
            y: -20,
            repeat: -1,
            yoyo: true,
            ease: "power1.inOut",
            duration: 1
        });
    });

    //gsap.to(".box", { rotation: 27, x: 100, duration: 1 });
    
    const quizData = [{
        question: "モンテカルロ法において、精度を上げる方法は次のうちどれ？",
        options: [
            { value: "option1", label: "サンプル数を増やす" ,correct:true},
            { value: "option2", label: "サンプル数を減らす" ,correct:false},
            { value: "option3", label: "サンプル数を一定にする" ,correct:false},
            { value: "option4", label: "サンプル数をランダムにする" ,correct:false}
        ],
        answer: "option1",
        collectMessage: "Unityのシミュレーションでモンテカルロ法を使用する場合、サンプル数を増やすことで精度が向上します。",
        incorrectMessage: "Unityでもう一度確認してみましょう！"
    },
    {
        question: "2.モンテカルロ法において、精度を上げる方法は次のうちどれ？",
        options: [
            { value: "option1", label: "サンプル数を増やす" ,correct:true},
            { value: "option2", label: "サンプル数を減らす" ,correct:false},
            { value: "option3", label: "サンプル数を一定にする" ,correct:false},
            { value: "option4", label: "サンプル数をランダムにする" ,correct:false}
        ],
        answer: "option1"

    }];
    let userSelectedOptions = [
        { questionIndex: 0, selectedOption: null },
        { questionIndex: 1, selectedOption: null }
    ]
    const selectedOption = ref("option1")
    const switchDisplay = ref(true)
    const isLastQuestion = ref(false)
    const questionIndex = ref(0)
    const totalQuestions = quizData.length
    const isCorrect = ref(false)

    const showQuiz = ref(true)
    const showResult = ref(false)
    const showFinalResult = ref(false)


    function handleAnswer() {
        switchDisplay.value = false

        showQuiz.value = false
        showResult.value = true

        quizData[questionIndex.value].options.forEach(option => {
            if(option.value === selectedOption.value) {
                isCorrect.value = option.correct
                userSelectedOptions[questionIndex.value].selectedOption = option.value
            }
        })
        console.log("Selected option:", selectedOption.value);
    }
    async function handleNext() {
        // 次の問題に進むロジックをここに追加
        questionIndex.value += 1
        if(questionIndex.value+1 >= totalQuestions) {
            isLastQuestion.value = true
        }
        switchDisplay.value = true
        showQuiz.value = true
        showResult.value = false
        await nextTick()
        tl.clear() // アニメーションをクリアして次の問題に移る際に前のアニメーションが残らないようにする
        tl.restart() // アニメーションをリスタートして次の問題に移る際にアニメーションが再度動くようにする
    }
    function handleFinish() {
        showResult.value = false
        showFinalResult.value = true
    }
</script>
<template>
    
    <div class=" min-h-screen w-[80%] mx-auto max-w-[800px] flex flex-col justify-center">
        <div v-if="showQuiz">
            <h1 class="text-2xl font-bold">第{{questionIndex+1}}問</h1>
            <p class="text-2xl mt-8">{{ quizData[0].question }}</p>
            <div class="mt-12">
                <UAlert
                    title="ヒント"
                    description="Unityのシミュレーションでモンテカルロ法を使用する場合、サンプル数を増やすことで精度が向上します。"
                    color="neutral"
                    variant="outline"
                />
            </div>
            <div class=" mt-8">
                <URadioGroup v-model="selectedOption" color="primary" variant="card" default-value="option1" :items="quizData[questionIndex].options" />
            </div>
            <div class=" mt-12">
                <UButton size="xl" @click="handleAnswer">回答</UButton>
            </div>
        </div>
        <div v-if="showResult">
            <h1 class=" text-2xl font-bold">第{{questionIndex+1}}問</h1>
            <p class="text-2xl mt-8">{{quizData[questionIndex].question}}</p>
            <div class="mt-12">
                <UAlert
                    :title="isCorrect ? '正解!' : '不正解'"
                    description="Unityのシミュレーションでモンテカルロ法を使用する場合、サンプル数を増やすことで精度が向上します。"
                    color="neutral"
                    variant="outline"
                />
                
            </div>
            <div class="flex flex-col gap-3.5 mt-8" >
            <div>
                <QuizResult v-if="isCorrect" />
                <UBadge size="md" v-if="!isCorrect" color="neutral" variant="soft" class="font-bold my-2 rounded-full">不正解</UBadge>
                <URadioGroup v-model="selectedOption" indicator="hidden" :color="isCorrect ? 'primary' : 'neutral'" variant="card" default-value="option1" :items="quizData[questionIndex].options" disabled />
            </div>
            
            </div>
            <div class=" mt-12">
                <UButton v-if="!isLastQuestion" size="xl" @click="handleNext">次の問題へ</UButton>
                <UButton v-else size="xl" @click="handleFinish">結果を見る</UButton>
            </div>
        </div>
        <div v-if="showFinalResult" class="flex flex-col items-center gap-8">
            <h1 class=" text-3xl font-bold">最終結果</h1>
            <p class="text-xl">あなたの正解数は {{ userSelectedOptions.filter(option => option.selectedOption === quizData[option.questionIndex].options.find(o => o.correct).value).length }} / {{ totalQuestions }} です！</p>
            <div class="flex flex-col gap-3.5 mt-8" >
                <div v-for="(option, index) in quizData[0].options">
                    <UBadge v-if="option.correct" size="md" variant="soft" class="font-bold my-2 rounded-full">正解!</UBadge>
                    <UPageCard
                    :key="index"
                    :title="option.label"
                    :highlight="option.correct"
                    variant="outline"
                    />
                </div>
            </div>
        </div>
    </div>
</template>