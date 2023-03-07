<template>
    <div class="container shadow px-4 py-2 mt-4" v-if="showForm">
        <h5 class="my-4 text-info">Tambahkan menu</h5>
        <form>
            <div class="mb-3">
                <label for="title" class="form-label">Nama menu *</label>
                <input type="text" class="form-control" id="title" required>
            </div>
            <div class="mb-5">
                <label for="formFileMultiple" class="form-label">Foto *</label>
                <input class="form-control" type="file" id="formFileMultiple" multiple>
            </div>
            <div class="input-group mb-3">
                <span class="input-group-text bg-info text-white" id="harga">Rp.</span>
                <input type="number" class="form-control" aria-label="Harga" aria-describedby="harga">
            </div>
            <div class="mb-3 d-flex justify-content-end">
                <button type="submit" class="btn btn-success " @click="showForm = false">Simpan</button>
            </div>
        </form>
    </div>
    <div class="container" v-else>
        <p class="my-4 text-muted">Tambahkan menu makanan yang ada di resto</p>
        <div class="container shadow p-4">
            <button type="button" class="my-3 btn btn-info text-white btn-md" @click="showForm = true" v-if="!showForm">+
                Tambah Menu</button>
            <table class="table table-striped">
                <thead>
                    <tr>
                        <th scope="col">#</th>
                        <th scope="col">Nama</th>
                        <th scope="col">Foto</th>
                        <th scope="col">Harga</th>
                    </tr>
                </thead>
                <tbody class="align-items-center justify-content-center">
                    <tr v-for="(item, index) in foods" :key="index">
                        <th scope="row">{{ index + 1 }}</th>
                        <td>{{ item.name }}</td>
                        <td><img :src="item.image" alt="food-image" width="50" height="50">
                        </td>
                        <td>Rp.{{ item.price.toLocaleString() }}</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            foods: [
                { name: "Nasi Goreng", price: 15000, image: "https://picsum.photos/id/100/300/200" },
                { name: "Mie Ayam", price: 12000, image: "https://picsum.photos/id/200/300/200" },
                { name: "Soto Ayam", price: 20000, image: "https://picsum.photos/id/400/300/200" },
                { name: "Tempe Goreng", price: 20000, image: "https://picsum.photos/id/500/300/200" },
                { name: "Nasi Pecel", price: 20000, image: "https://picsum.photos/id/600/300/200" },
                { name: "Sayur Bayam", price: 20000, image: "https://picsum.photos/id/700/300/200" },
            ],
            showForm: false,
        }
    },
}
</script>