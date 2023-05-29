<template>
    <ul class="navigation">
        <li v-for="link in links" :key="link.id">
            <a :href="link.href" cursor-target>{{ link.name }}</a>
        </li>
    </ul>
</template>

<script>
export default {
    name: 'Navbar',
    data: () => ({
        links: [
            {
                id: 1,
                href: '#',
                name: 'Заклади'
            },
            {
                id: 2,
                href: '#',
                name: 'Доставка і оплата'
            },
            {
                id: 3,
                href: '#',
                name: 'Акції'
            },
            {
                id: 4,
                href: '#',
                name: 'Про нас'
            }
        ]
    }),
}
</script>

<style lang="scss" scoped>
@import "./Navbar.scss";
</style>
