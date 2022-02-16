<template>
     <footer class="main-footer">
            <strong>Copyright &copy; 2014-{{currentDate.getFullYear()}} <Link href="#">BaseCrud</Link>.</strong>
            Todos os direitos reservados.
            <div class="float-right d-none d-sm-inline-block">
            <b>Versão</b> 1.0
            </div>
        </footer>
</template>
<script>
import {Link} from '@inertiajs/inertia-vue3';
export default {
    
    data(){
        return {
            currentDate: new Date,
        }
    },
    components: {
        Link
    }
}
</script>