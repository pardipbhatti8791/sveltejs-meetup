<script>
    import Header from './UI/Header.svelte'
    import MeetupGrid from './Meetups/MeetupGrid.svelte'
    import TextInput from './UI/TextInput.svelte'
    import Button from './UI/Button.svelte'

    let title = '';
    let subtitle = ''
    let email = ''
    let imageUrl = ''
    let description = ''
    let address = ''


    let meetups = [
        {
            id: 'm1',
            title: 'Coding boot camp',
            subTitle: 'Learn to code in 2 hours',
            description: 'In this meetup, we will tell you how to code',
            imageUrl: 'https://m-square.com.au/wp-content/uploads/2018/04/mulesoft-meetups-2018-1-1.png',
            address: '27th Nerd Road, India',
            contactEmail: 'code@test.com'
        },
        {
            id: 'm2',
            title: 'Svelte boot camp',
            subTitle: 'Learn to swimming in 3 hours',
            description: 'In this meetup, we will tell you how svelte work',
            imageUrl: 'https://techbeacon.scdn7.secure.raxcdn.com/sites/default/files/styles/article_hero_image/public/field/image/keep-diverse-developer-hires.jpg?itok=6a82rhmr',
            address: '27th Nerd Road, India',
            contactEmail: 'svelte@test.com'
        },
        {
            id: 'm3',
            title: 'Swift boot camp',
            subTitle: 'Learn to code in 2 hours',
            description: 'In this meetup, we will tell you how to use swfit storyboard',
            imageUrl: 'https://www.productplan.com/uploads/2017/01/What-Developers-Would-Tell-Product-Managers-1024x641.jpeg',
            address: '27th Nerd Road, India',
            contactEmail: 'swift@test.com'
        }
    ]

    function addMeetup() {
        const newMeetup = {
            id: Math.random().toString(),
            title: title,
            subTitle: subtitle,
            description: description,
            imageUrl: imageUrl,
            contactEmail: email,
            address: address
        }
        meetups = [...meetups, newMeetup]
    }
</script>

<Header/>

<main>
    <form on:submit|preventDefault={addMeetup}>
        <TextInput id="title" type="text" label="Title" value="{title}" on:input="{event => (title = event.target.value)}"/>
        <TextInput id="subtitle" type="text" label="Sub Title" value="{subtitle}"
                   on:input="{event => (subtitle = event.target.value)}"/>
        <TextInput id="address" type="text" label="Address" value="{address}" on:input="{event => (address = event.target.value)}"/>
        <TextInput id="imageUrl" type="text" label="Image URL" value="{imageUrl}"
                   on:input="{event => (imageUrl = event.target.value)}"/>
        <TextInput id="email" type="email" label="Email" value="{email}" on:input="{event => (email = event.target.value)}"/>
        <TextInput id="description" label="Description" value="{description}"
                   on:input="{event => (description = event.target.value)}" rows="{3}" controlType="textarea"/>
        <Button type="submit" caption="Save" />
    </form>
    <MeetupGrid {meetups}/>
</main>

<style>
    main {
        margin-top: 5rem;
    }
</style>