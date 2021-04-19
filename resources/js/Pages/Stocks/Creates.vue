<template>
    <div>
        <Layout>
            <div class="flex justify-center w-full">
                <div class="bg-white flex flex-col w-1/3 mt-20 p-6">
                    <h2 class="text-lg">Stock Category Form</h2>
                    <form
                        id="stock-form"
                        name="stock-form"
                        v-on:submit.prevent="submit"
                    >
                        <div class="flex flex-col pt-6">
                            <label for="id">ID</label>
                            <input
                                type="text"
                                id="id"
                                name="id"
                                v-model="form.id"
                                autocomplete="off"
                            />
                            <div class="text-red-700 text-sm">
                                {{ errors.id }}
                            </div>
                            {{ form.id }}
                        </div>

               

                         <div class="flex flex-col pt-6">
                            <label for="stock_category_id">Stock Category Id</label>
               <select name="stock_category_id" id="stock_category_id" v-model="form.stock_category_id">
                    <option v-for="item in stock_categories"
                :key="item.id">{{ item.id }}</option>
                </select>
<!-- 
                   <label for="id">Stock Category ID</label>
                            <input
                                type="text"
                                id="stock_category_id"
                                name="stock_category_id"
                                v-model="form.stock_category_id"
                                autocomplete="off"
                            />

                            <div class="text-red-700 text-sm">
                                {{ errors.stock_category_id }}
                            </div>
                            {{ form.stock_category_id }} -->

                            <div class="text-red-700 text-sm">
                                {{ errors.type }}
                            </div>
                        </div>

                        <div class="flex flex-col pt-6">
                            <label for="description">Description</label>
                            <input
                                type="text"
                                id="description"
                                name="description"
                                v-model="form.description"
                                autocomplete="off"
                            />
                            <div class="text-red-700 text-sm">
                                {{ errors.description }}
                            </div>
                            {{ form.description }}
                        </div>

                     <div class="flex flex-col pt-6">
                            <label for="uom">UOM</label>
                            <input
                                type="text"
                                id="uom"
                                name="uom"
                                v-model="form.uom"
                                autocomplete="off"
                            />
                            <div class="text-red-700 text-sm">
                                {{ errors.uom }}
                            </div>
                             {{ form.uom }}
                        </div>

                            <div class="flex flex-col pt-6">
                            <label for="barcode">Barcode</label>
                            <input
                                type="text"
                                id="barcode"
                                name="barcode"
                                v-model="form.barcode"
                                autocomplete="off"
                            />
                            <div class="text-red-700 text-sm">
                                {{ errors.barcode }}
                            </div>
                             {{ form.barcode }}
                        </div>

                          


                          <div class="flex flex-col pt-6">
                            <label for="discontinued">Discontinue</label> </div>
                            <input
                                type="checkbox"
                                id="discontinued"
                                name="discontinued"
                                v-model="form.discontinued"
                                autocomplete="off"
                            />
                            Yes
                            <div class="text-red-700 text-sm">
                                {{ errors.discontinued }}
                            </div>


                            <!-- <input
                                type="checkbox"
                                id="discontinued"
                                name="discontinued"
                                value="N"
                                v-model="form.discontinued"
                                autocomplete="off"
                            />
                           No
                            <div class="text-red-700 text-sm">
                                {{ errors.discontinued }}
                            </div> -->

                      

                        <div class="flex flex-col pt-6">
                            <button
                                type="submit"
                                class="bg-indigo-800 text-white p-2"
                            >
                                Save
                            </button>
                        </div>
                    </form>
                </div>
            </div>
        </Layout>
    </div>
</template>

<script>
import { ref, reactive } from "vue";
import Layout from "@/Layouts/Authenticated";
import { Inertia } from "@inertiajs/inertia";

export default {
    components: {
        Layout,
        
    
    },

    props: {
        errors: Object,
       stock_categories: Array,
    success:String,
         
    },

    setup(props, context) {
        const form = reactive({
            id: null,
            stock_category_id: '1234',
            description: null,
            uom: null,
            barcode: null,
            discontinued: 'N',
       
        }); 

        const submit = () => {
            Inertia.post(route("stock.store"), form, {
                onSuccess: () => {
                    // Handle success event
                    form.id = null;
                    stock_category_id = '1234';
                    form.description = null;
                    form.uom = null;
                    form.barcode = null;
                    form.discontinued = 'N';
            

                    //   this.reset();
                },
            });
        };

        return {
            form,
            submit,
        };
    },
};
</script>
