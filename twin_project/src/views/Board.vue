<script setup>
import AddIcon from '../components/icons/AddIcon.vue';
import DeleteIcon from '../components/icons/DeleteIcon.vue'; 
import EditIcon from '../components/icons/EditIcon.vue';
</script>

<template>
    <section class="vh-100 gradient-custom-2">
        <div class="container py-5 h-100">
            <div class="row d-flex justify-content-center align-items-center h-100">
                <div class="col-md-12 col-xl-10">
                    <div class="card mask-custom">
                        <div class="card-body p-4 text-white">

                            <div class="text-center pt-3 pb-2">
                            <img src="https://mdbcdn.b-cdn.net/img/Photos/new-templates/bootstrap-todo-list/check1.webp"
                                alt="Check" width="60">
                            <h2 class="my-4">Task Board</h2>
                            </div>

                            <div class="table-div">
                                <table class="table text-white mb-0 table-body">
                                <thead>
                                    <tr>
                                    <th scope="col">Task</th>
                                    <th scope="col">Description</th>
                                    <th scope="col">Status</th>
                                    <th scope="col">Actions</th>
                                    </tr>
                                </thead>
                                <tbody>
                                    <tr class="fw-normal">
                                        <th>
                                            <span class="ms-2">Alice Mayer</span>
                                        </th>
                                        <td class="align-middle">
                                            <span>Call Sam For payments</span>
                                        </td>
                                        <td class="align-middle">
                                            <h6 class="mb-0"><span>High priority</span></h6>
                                        </td>
                                        <td>
                                            <div class="actions">
                                            <a href="#!" data-mdb-toggle="tooltip" @click="openModal('delete')" title="delete"><DeleteIcon></DeleteIcon></a>
                                            <a href="#!" data-mdb-toggle="tooltip" @click="openModal('edit')" title="edit"><EditIcon></EditIcon></a>
                                            </div>
                                        </td>
                                    </tr>
                                </tbody>
                                </table>
                            </div>
                            <div class="d-flex justify-content-end mt-4">
                            <a href="#!" @click="openModal('add')" class="task-add" data-mdb-toggle="tooltip" title="Add">
                                <AddIcon></AddIcon>
                                <span class="m-2" style="font-weight: bold;">Task</span>
                            </a>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
    <Modal ref="modal"></Modal>
</template>

<script>
    import Modal from './Modal.vue';
    import AddTask from '@/components/AddTask.vue';
    import DeleteTask from '@/components/DeleteTask.vue';
    import EditTask from '@/components/EditTask.vue';
    
    export default {
        components: {
            Modal,
            AddTask,
            DeleteTask,
            EditTask
        },
        methods: {
            openModal(type) {
                let dynamicComponent = null;
                let header = "Título Padrão";

                switch (type) {
                    case "add":
                        dynamicComponent = AddTask;
                        header = "Create new Task";
                    break;
                    case "delete":
                        dynamicComponent = DeleteTask;
                        header = "Delete Task";
                    break;
                    case "edit":
                        dynamicComponent = EditTask;
                        header = "Edit Task";
                    break;
                }

                this.$refs.modal.openModal({ component: dynamicComponent, header });
            }
        }
    };
</script>