<template>
      <nav class="navbar header fixed-top" id="myHeader" style="background-color: #E5B844; height: 10vh;">
            <div class="container-fluid dua">
               <div class="d-flex mb-3"></div>
               <div class="p-2"><b><i class="bi bi-list tiga"></i></b></div>
               <div class="p-2"><strong class="tiga">ABSENSI KELAS</strong></div>
               <div class="ms-auto p-2"><img :src="fotoProfil" width="50px" height="50px"></div>
            </div>
      </nav>
</template>

<script setup>
const supabase = useSupabaseClient()
const user = useSupabaseUser()

const fotoProfil = ref('')

const getFotoProfil = async () => {
   const { data, error } = await supabase.from('siswa').select('FotoProfil').eq('uid', user.value.id).single()
   if (error) throw error
   if (data) fotoProfil.value = data.FotoProfil
}

onMounted(() => {
   getFotoProfil()
})
</script>

<style scoped>
.dua{
   font-size: 30px;
}
.tiga{
   padding-left: 10px;
   font-family: 'Montserrat', sans-serif;
}
.empat{
   padding-right: 10px;
}
img{
   border-radius: 25px;
}
</style>