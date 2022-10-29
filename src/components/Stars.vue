<template>
    <div>
        <svg class="star" :fill="starColor" width="40" height="40" viewBox="0 0 24 24"
            xmlns="http://www.w3.org/2000/svg">
            <path
                d="M12.5 17.925 6.629 21l1.121-6.512L3 9.875l6.564-.95L12.5 3l2.936 5.925 6.564.95-4.75 4.613L18.371 21z" />
        </svg>
        <svg class="star" :fill="starColor" width="50" height="50" viewBox="0 0 24 24"
            xmlns="http://www.w3.org/2000/svg">
            <path
                d="M12.5 17.925 6.629 21l1.121-6.512L3 9.875l6.564-.95L12.5 3l2.936 5.925 6.564.95-4.75 4.613L18.371 21z" />
        </svg>
        <svg class="star" :fill="starColor" width="40" height="40" viewBox="0 0 24 24"
            xmlns="http://www.w3.org/2000/svg">
            <path
                d="M12.5 17.925 6.629 21l1.121-6.512L3 9.875l6.564-.95L12.5 3l2.936 5.925 6.564.95-4.75 4.613L18.371 21z" />
        </svg>
    </div>
</template>

<script>
export default {
    props: {
        starColor: {
            type: String

        }
    }

}
</script>

