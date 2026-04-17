<script setup>
    import { gsap } from "gsap";

    onMounted(() => {
        gsap.from(".animate", {
            y: 20,
            scale:0.3,
            ease: "back.out(1.7)",
            duration: 0.5
        });
    });
</script>
<template>
    <UBadge size="md" variant="soft" class="animate font-bold my-2 rounded-full">正解!</UBadge>
</template>