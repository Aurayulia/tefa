<template>
    <div class="container-fluid">
        <div class="row">
            <div class="col-lg-12">
                <h2 class="text-center my-4">ISI BUKU KUNJUNGAN</h2>
                <form>
                    <div class="mb-3"></div>
                        <input type="text" class="form-control form-control-lg rounded-5" placeholder="Nama">

                    <div class="mb-3">
                        <select class="form-control form-control-lg form-select rounded-5">
                            <option value="">KEANGGOTAAN</option>
                            <option value="Siswa">Siswa</option>
                            <option value="Guru">Guru</option>
                            <option value="Staf">Staf</option>
                            <option value="Umum">Umum</option>                                    
                        </select>
                    </div>

                    <div class="mb-3">
                        <div class="row">
                            <div class="col-md-4">
                                <select class="form-control form-control-lg form-select rounded-5 mb-2">
                                    <option value="">TINGKAT</option> 
                                    <option value="X">X</option>    
                                    <option value="XI">XI</option>    
                                    <option value="XII">XII</option>  
                                </select>
                            </div>

                            <div class="col-md-4">
                                <select class="form-control form-control-lg form-select rounded-5 mb-2">
                                    <option value="">KELAS</option>
                                    <option value="1">1</option>
                                    <option value="2">2</option>
                                    <option value="3">3</option>
                                    <option value="4">4</option>
                                </select>
                            </div>

                            <div class="col-md-4">
                                <select class="form-control form-control-lg form-select rounded-5 mb-2">
                                    <option value="">JURUSAN</option>
                                    <option value="PPLG">PPLG</option>
                                    <option value="TJKT">TJKT</option>
                                    <option value="TSM">TSM</option>
                                    <option value="DKV">DKV</option>
                                    <option value="TOI">TOI</option>
                                </select>
                            </div>

                            <div class="mb-3">
                                <select class="form-control form-control-lg form-select rounded-5">
                                    <option value="">KEPERLUAN</option>
                                    <option value="baca">Baca Buku</option>
                                    <option value="pinjam">Pinjam</option>
                                    <option value="kembalikan">Kembalikan Buku</option> 
                                </select>
                            </div>

                            <div>
                                <nuxt-link to="../pengunjung" class="btn btn-dark btn-lg rounded-5 px-5">Kirim</nuxt-link>
                            </div>

                        </div>
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>


<script setup>
const supabase = useSupabaseClient()

const member = ref([])
const oobjectives = ref([]) 

<script setup>
const form =ref({
    nama: "",
    keanggotaan: "",
    tingkat: "",
    jurusan: "",
    kelas: "",
    keperluan: "",
})


const kirimData = async() => {
    const { error } = await supabase.from('pengunjung').insert{[from.value]}
    if (!error) navigateTo('/pengunjung')
 }

const getKeanggotaan = async () => {
    const { data, error } = await supabase.from('keanggotaan').select('*')
    if(data) members.value = data
}

const getKeperluan = async () => {
    const { data, error } =await supabase.from('keperluan').select('*')
    if (data) objectives.value = data      
}

onMounted(() => {
    getKeanggotaan()
    getKeperluan()
})
</script>

