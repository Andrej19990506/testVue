<template >
    <div class="alert alert-success d-flex align-items-center" role="alert">
        <svg class="bi flex-shrink-0 me-2" version="1.1" id="Capa_1" xmlns="http://www.w3.org/2000/svg"
            xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" viewBox="0 0 50 50"
            style="enable-background:new 0 0 50 50;" xml:space="preserve">
            <circle style="fill:#25AE88;" cx="25" cy="25" r="25" />
            <polyline
                style="fill:none;stroke:#FFFFFF;stroke-width:2;stroke-linecap:round;stroke-linejoin:round;stroke-miterlimit:10;"
                points="
	38,15 22,33 12,25 " />
        </svg>

        <div class="alert__title">
            Товар успешно добавлен
        </div>

    </div>
</template>
<script>
export default {
    data() {
        return {
        }
    }
}
</script>
<style lang="scss">



.alert {
    height: 50px;
    z-index: 2;
    top: 18px;
    width: 327px;
    box-shadow: 0px 2px 14px #0f5132;
    outline: 1px solid #089f58;
    position: fixed !important;
}

.me-2 {
    width: 15px;
}

.alert__title {
    margin-left: 35px;
}
</style>
