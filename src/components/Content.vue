<template>
    <div>
        <!-- Container -->
        <div class="container mx-auto text-center">
            <p class="mt-10">you answered : 0/10</p>
            <!-- Question -->
            <h1 class="my-10 mx-[2rem]">Questions :</h1>

            <hr class="mb-10">

            <!-- Answers container -->
            <div class="grid md:grid-cols-2 place-items-center md:mx-[-1.25rem] lg:mx-[5rem] xl:mx-[13rem]">

                <!-- answer -->
                <button class="w-[25rem] h-[6rem] rounded-lg border border-pink-600 mb-3 md:mb-[6rem] ">
                    <p class="text-center px-2 py-7">Asnwers</p>
                </button>
                <button class="w-[25rem] h-[6rem] rounded-lg border border-pink-600 mb-3 md:mb-[6rem] ">
                    <p class="text-center px-2 py-7">Asnwers</p>
                </button>
                <button class="w-[25rem] h-[6rem] rounded-lg border border-pink-600 mb-3 md:mb-[6rem] ">
                    <p class="text-center px-2 py-7">Asnwers</p>
                </button>
                <button class="w-[25rem] h-[6rem] rounded-lg border border-pink-600 mb-3 md:mb-[6rem] ">
                    <p class="text-center px-2 py-7">Asnwers</p>
                </button>
            </div>

            <!-- Buttons -->
            <div class="flex flex-row items-center justify-center mt-5">
                <!-- Submit button -->
                <button class="w-[6rem] h-[3rem] bg-violet-600 mr-5">
                    <p class="text-center px-2 py-1 text-white">Submit</p>
                </button>
                <!-- Next button -->
                <button class="w-[6rem] h-[3rem] bg-green-500">
                    <p class="text-center px-2 py-1 text-white">Next</p>
                </button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'ContentSection',

}
</script>