<template>
      <div class="container-fluid">
        <div class="row">
          <div class="col-lg-6">
            <nuxt-link to="/pengunjung/tambah">
                  <div class="card bg-pengunjung rounded-5">
                    <div class="card-body">
                      <h2>Pengunjung</h2>
                    </div>
                  </div>
            </nuxt-link>
          </div>

               <div class="col-lg-6">
                      <nuxt-link to="/buku">
                           <div class="card bg-buku rounded-5">
                              <div class="card-body">
                                 <h2>Cari Buku</h2>
                             </div>
                         </div>
                    </nuxt-link>
                </div>
          </div>
        </div>

        <h1 class="statistik">STATISTIK</h1>
        <div class="row">
          <div class="col-lg-6">
            <nuxt-link to ="/pengunjung">
                        <div class="card bg-warning rounded-5">
                            <div class="card-body">
                                <h1 class="font">7 pengunjung</h1>
                            </div>
                        </div>
            </nuxt-link>
          </div>
               <div class="col-lg-6">
                      <nuxt-link to ="/buku">
                        <div class="card bg-success  rounded-5">
                            <div class="card-body">
                                <h1 class="font">7 Buku</h1>
                            </div>
                        </div>
                    </nuxt-link>
                </div>
          </div>
        

          <!-- <div class="row my-5">
              <div class="col-lg-6">
                        <div class="card bg-warning rounded-5"><h1 style="font-size: 120px;">{{ jumlah }}</h1></div>
                        <div class="col mt-5 p-5"><h2 style="font-family: margin-left -20px">Buku</h2></div>
                            <div class="card-body">
                                <h2 class="font"> 3 pengunjung</h2>
                            </div>
                        </div>
              </div>
          

              <div class="col-lg-6">
                    <nuxt-link to ="/buku">
                        <div class="card bg-success  rounded-5">
                            <div class="card-body">
                                <h1 class="font">7 Buku</h1>
                            </div>
                        </div>
                    </nuxt-link>
              </div> -->
              <div>
                <Chart />
              </div>

</template>


<script setup>
const supabase = useSupabaseClient();
const jumlahp = ref(0);
const jumlahb = ref(0);

async function ambiljumlahp () {
  const  {data,error,count} = await supabase
  .from("pengunjung")
  .select("*", {count: "exact"});
 if (count) jumlahb.value = count; 
};

async function ambiljumlahb () {
  const  {data, error,count} = await supabase
    .from("buku")
    .select("*", {count: "exact"});
   if (count) jumlahb.value = count; 
};

onMounted(() => {
  ambiljumlahp();
  ambiljumlahb();
})
</script>
<style scoped>
.card {
   height: 250px;
   box-shadow: 3px 1px 10px #424242;
}
.card.bg-pengunjung {
     margin-top: 5%;
     background-image: url('../assets/img/bg-home-kunjungan (3).jpeg');
     background-repeat: no-repeat;
     background-position: center center;
     background-size: cover;
     opacity: 90%;

}

.card.bg-buku {
  margin-top: 5%;
  background: url('../assets/img/bg-home-cari-buku.jpg');
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
  opacity: 90%;
}
h2{
  color: black;
  font: arial;
}
h1{
  color: white;
}
.card.bg-success{
  margin-top: 2%;
}
.statistik{
  margin-top: 5%;
  color: black;
  font: arial;
}
.font{
  text-align: center;
  margin-top: 80px;
  font-size: 250%;
  color: black;
}
.bg-warning{
  margin-top: 2%;
}
</style>
