<script setup>
import { defineComponent, reactive, ref } from 'vue';
let check = ref(false)

let formData = {
    eesnimi: "",
    perekonnanimi: "",
    email: "",
    telefon: "",
    aadress1: "",
    aadress2: "",
    maakond: "",
    linn: "",
    ettevote: "",
    regkood: "",
    postiindeks: "",
    parool: "",
    parool2: "",
};

function handleSubmit(){
            // Perform form validation logic here
            if (formData.eesnimi.length === 0 || formData.perekonnanimi.length === 0) {
                console.log('Please enter both ees- ja perekonnanimi name');
                return;
            }

            // Perform form submission logic here
            console.log(`Form submitted with data: ${JSON.stringify(formData)}`);
        }; 
</script>

<template>
    <html data-theme="dark">
    <main class="w-full min-h-screen pt-[5rem] flex-col px-[15%] justify-center m-auto">

        <ul class="steps w-[100%] py-[1rem] mt-12 mb-4">
            <li class="step step-primary">Domeeni Valimine</li>
            <li class="step step-primary">Info</li>
            <li class="step">Maksmine</li>
        </ul>

        <!-- Domeenid -->
        <form class="flex 2xl:flex-row flex-col gap-8 w-[100%]" @submit.prevent="handleSubmit()">
            <div class="2xl:w-[55%] w-full mx-2">
                <div class="mb-4">
                    <div class="rounded-t-md text-xl font-semibold p-4 bg-zinc-900">Personaalne Informatsioon</div>
                    <table class="table table-md bg-zinc-900/50 rounded-md rounded-t-none">
                        <tbody>
                            <!-- row 1 -->
                            <tr class="border-0">
                                <td class="flex content-center gap-2">
                                    <input type="text" placeholder="Eesnimi*" v-model="formData.eesnimi"
                                        class="input input-bordered input-primary w-full max-w-lg m-auto invalid:input-error"
                                        required />
                                    <input type="text" placeholder="Perekonnanimi*" v-model="formData.perekonnanimi"
                                        class="input input-bordered input-primary w-full max-w-lg m-auto invalid:input-error"
                                        required />
                                </td>
                                <td class="flex content-center gap-2">
                                    <input type="email" placeholder="Email*" v-model="formData.email"
                                        class="input input-bordered input-primary w-full max-w-lg m-auto invalid:input-error"
                                        required />
                                    <input type="tel" placeholder="Telefon*" v-model="formData.telefon"
                                        class="input input-bordered input-primary w-full max-w-lg m-auto invalid:input-error"
                                        required />
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </div>
                <div class="mb-4">
                    <div class="rounded-t-md text-xl font-semibold p-4 bg-zinc-900">Billing</div>
                    <table class="table table-md bg-zinc-900/50 rounded-md rounded-t-none">
                        <tbody>
                            <!-- row 1 -->
                            <tr class="border-0">
                                <td class="flex content-center gap-2">
                                    <input type="text" placeholder="Aadress 1*" v-model="formData.aadress1"
                                        class="input input-bordered input-primary w-full max-w-lg m-auto invalid:input-error"
                                        required />
                                    <input type="text" placeholder="Aadress 2 (valikuline)" v-model="formData.aadress2"
                                        class="input input-bordered input-primary w-full max-w-lg m-auto" />
                                </td>
                                <td class="flex content-center gap-2">
                                    <input type="text" placeholder="Maakond*" v-model="formData.maakond"
                                        class="input input-bordered input-primary w-full max-w-lg m-auto invalid:input-error"
                                        required />
                                    <input type="text" placeholder="Linn*" v-model="formData.linn"
                                        class="input input-bordered input-primary w-full max-w-lg m-auto invalid:input-error"
                                        required />
                                </td>
                                <td v-if="check" class="flex content-center gap-2">
                                    <input type="text" placeholder="Ettevõtte nimi*" v-model="formData.ettevote"
                                        class="input input-bordered input-primary w-full max-w-lg m-auto invalid:input-error"
                                        required />
                                    <input type="text" placeholder="Ettevõtte reg. kood*" v-model="formData.regkood"
                                        class="input input-bordered input-primary w-full max-w-lg m-auto invalid:input-error"
                                        required />
                                </td>
                                <td class="flex content-center gap-2">
                                    <input type="text" placeholder="Postiindeks*" v-model="formData.postiindeks"
                                        class="input input-bordered input-primary w-full max-w-lg m-auto invalid:input-error"
                                        required />
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </div>
                <div class="flex items-center mb-4">
                    <label class="label cursor-pointer">
                        <input type="checkbox" @click="check = !check" class="checkbox checkbox-primary checkbox-lg" />
                        <span class="ml-4 select-none text-lg">Ettevõte</span>
                    </label>
                </div>
                <div class="mb-4">
                    <div class="rounded-t-md text-xl font-semibold p-4 bg-zinc-900">Konto</div>
                    <table class="table table-md bg-zinc-900/50 rounded-md rounded-t-none">
                        <tbody>
                            <!-- row 1 -->
                            <tr class="border-0">
                                <td class="flex content-center gap-2">
                                    <input type="password" placeholder="Parool*" v-model="formData.parool"
                                        class="input input-bordered input-primary w-full max-w-lg m-auto invalid:input-error"
                                        required />
                                    <input type="password" placeholder="Kinnita Parool*" v-model="formData.parool2"
                                        class="input input-bordered input-primary w-full max-w-lg m-auto invalid:input-error"
                                        required />
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>


            <!-- Ostukorv ja nupp -->
            <div class="2xl:w-[45%] w-full mx-2">

                <div class="rounded-t-md text-xl font-semibold p-4 bg-zinc-900">Ostukorv</div>
                <table class="table table-fixed table-md bg-zinc-900/50 rounded-md rounded-t-none">
                    <!-- head -->
                    <thead class="">
                        <tr class="border-zinc-900">
                            <th>Domain</th>
                            <th>Price</th>
                            <td class="flex content-end">
                                <label class="ml-auto">
                                    <button type="button"
                                        class="btn btn-error btn-outline btn-sm max-2xl:btn-square whitespace-normal overflow-x-auto"><span
                                            class="max-2xl:hidden">Remove
                                            everything</span>
                                        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 2xl:hidden" fill="none"
                                            viewBox="0 0 24 24" stroke="currentColor">
                                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                                d="M6 18L18 6M6 6l12 12" />
                                        </svg>
                                    </button>
                                </label>
                            </td>
                        </tr>
                    </thead>
                    <tbody>
                        <!-- row 1 -->
                        <tr class="border-zinc-900">
                            <td>
                                <div class="flex items-center gap-3">
                                    <div>
                                        <div class="font-bold">Name.com</div>
                                    </div>
                                </div>
                            </td>
                            <td>
                                <span class="badge badge-accent badge-lg">350€</span>
                                <span class="text-lg">/ year</span>
                            </td>
                            <td class="flex content-end">
                                <label class="ml-auto">
                                    <button type="button"
                                        class="btn btn-error btn-outline btn-sm max-2xl:btn-square whitespace-normal overflow-x-auto"><span
                                            class="max-2xl:hidden">Remove</span>
                                        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 2xl:hidden" fill="none"
                                            viewBox="0 0 24 24" stroke="currentColor">
                                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                                d="M6 18L18 6M6 6l12 12" />
                                        </svg>
                                    </button>
                                </label>
                            </td>
                        </tr>
                        <!-- row 2 -->
                        <tr class="border-zinc-900">
                            <td>
                                <div class="flex items-center gap-3">
                                    <div>
                                        <div class="font-bold">Name.com</div>
                                    </div>
                                </div>
                            </td>
                            <td>
                                <span class="badge badge-accent badge-lg">350€</span>
                                <span class="text-lg">/ year</span>
                            </td>
                            <td class="flex content-end">
                                <label class="ml-auto">
                                    <button type="button"
                                        class="btn btn-error btn-outline btn-sm max-2xl:btn-square whitespace-normal overflow-x-auto"><span
                                            class="max-2xl:hidden">Remove</span>
                                        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 2xl:hidden" fill="none"
                                            viewBox="0 0 24 24" stroke="currentColor">
                                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                                d="M6 18L18 6M6 6l12 12" />
                                        </svg>
                                    </button>
                                </label>
                            </td>
                        </tr>

                    </tbody>
                    <tfoot>
                        <tr class="border-zinc-900 border-t">
                            <td>
                                <span class="text-lg">Kokku</span>
                            </td>
                            <td>
                                <span class="badge badge-accent badge-lg">700€</span>
                                <span class="text-lg">/ year</span>
                            </td>
                        </tr>
                    </tfoot>
                </table>
                <button type="submit" class="btn btn-primary btn-outline w-[100%] mt-[1rem] m-auto font-bold">JÄTKA</button>
                <button type="submit" @click="$router.push('/works/school/tailwind/domainstore1')"
                    class="btn btn-neutral btn-outline w-[100%] mt-[1rem] m-auto font-bold">TAGASI</button>

            </div>
        </form>

    </main>

    </html>
</template>

<style scoped>
#hider {
    display: none;
}
</style>