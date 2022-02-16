<template>
    <aside class="main-sidebar sidebar-dark-primary elevation-4">
            <!-- Brand Logo -->
            <Link  :href="route('admin.dashboard.index')" class="brand-link">
            <img :src="'/images/AdminLTELogo.png'" alt="AdminLTE Logo" class="brand-image img-circle elevation-3" style="opacity: .8">
            <span class="brand-text font-weight-light">AdminLTE 3</span>
            </Link >

            <!-- Sidebar -->
            <div class="sidebar">
            <!-- Sidebar user panel (optional) -->
            <div class="user-panel mt-3 pb-3 mb-3 d-flex">
                <div class="image">
                <img :src="'/images/user2-160x160.jpg'" class="img-circle elevation-2" alt="User Image">
                </div>
                <div class="info">
                <a href="#" class="d-block">{{$page.props.user.name}}</a>
                </div>
            </div>

            
            <!-- Sidebar Menu -->
            <nav class="mt-2">
                <ul class="nav nav-pills nav-sidebar flex-column" data-widget="treeview" role="menu" data-accordion="false">
                <!-- Add icons to the links using the .nav-icon class
                    with font-awesome or any other icon font library -->
                <li class="nav-item">
                    <Link :href="route('admin.dashboard.index')" class="nav-link" :class="{ 'active': route().current('admin.dashboard.*')}">
                    <i class="nav-icon fas fa-tachometer-alt"></i>
                    <p>
                        Dashboard
                    </p>
                    </Link>
                </li>
                <li class="nav-item">
                    <a href="#" class="nav-link">
                        <i class="nav-icon fas fa-table"></i>
                        <p>
                            Tables
                            <i class="fas fa-angle-left right"></i>
                        </p>
                    </a>                
                    <ul class="nav nav-treeview">
                    <li class="nav-item" v-if="$page.props.auth.hasRole.superAdmin || $page.props.auth.hasRole.admin || $page.props.auth.hasRole.moderator || $page.props.auth.hasRole.developer ">
                        <Link :href="route('admin.admins.index')" class="nav-link" :class="{ 'active': route().current('admin.admins.*')}">
                            <i class="far fa-circle nav-icon"></i>
                            <p>
                                Admins
                            </p>
                        </Link>
                    </li>
                    <li class="nav-item" v-if="$page.props.auth.hasRole.superAdmin || $page.props.auth.hasRole.admin || $page.props.auth.hasRole.moderator ">
                        <Link :href="route('admin.users.index')" class="nav-link" :class="{ 'active': route().current('admin.users.*')}">
                            <i class="far fa-circle nav-icon"></i>
                            <p>
                                Users
                            </p>
                        </Link>
                    </li>
                    <li class="nav-item" v-if="$page.props.auth.hasRole.superAdmin || $page.props.auth.hasRole.admin || $page.props.auth.hasRole.moderator ">
                        <Link :href="route('admin.roles.index')" class="nav-link" :class="{ 'active': route().current('admin.roles.*')}">
                            <i class="far fa-circle nav-icon"></i>
                            <p>
                                Roles
                            </p>
                        </Link>
                    </li>
                    <li class="nav-item" v-if="$page.props.auth.hasRole.superAdmin || $page.props.auth.hasRole.admin ">
                        <Link :href="route('admin.permissions.index')" class="nav-link" :class="{ 'active': route().current('admin.permissions.*')}">
                            <i class="far fa-circle nav-icon"></i>
                            <p>
                                Permissions
                            </p>
                        </Link>
                    </li>
                    </ul>
                </li>
                
                <li class="nav-header">MISCELLANEOUS</li>
                <li class="nav-item">
                    <Link :href="route('dashboard')" class="nav-link">
                    <i class="fas fa-home nav-icon"></i>
                    <p>Site</p>
                    </Link>
                </li>
                <li class="nav-item">
                    <Link @click="logout" class="nav-link" role="button">
                    <i class="fas fa-sign-out-alt nav-icon"></i>
                    <p>Logout</p>
                    </Link>
                </li>
                </ul>
            </nav>
            <!-- /.sidebar-menu -->
            </div>
            <!-- /.sidebar -->
        </aside>
</template>
<script>
import {Link} from '@inertiajs/inertia-vue3';
export default {
    components: {
        Link
    },
    mounted(){
        this.activeLink()
    },
    methods:{
        activeLink(){
            if($('.nav.nav-treeview .active').length){
                $('.nav.nav-treeview .active').parent().parent().parent().addClass('active menu-open')
                $('.nav.nav-treeview .active').parent().parent().css('display','block')
            }
        },
        logout(){
            this.$inertia.post('/logout')
        }
    }
    
}
</script>