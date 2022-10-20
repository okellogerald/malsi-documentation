<template>
    <Layout>

        <!-- Learn how to use images here: https://gridsome.org/docs/images -->
        <g-image alt="Logo" src="~/assets/images/favicon.png" width="135" />

        <h1>ARCHITECTURE / SOFTWARE DESIGN</h1>

        <h2>1/4: Architecture layers</h2>

        <p>
            Malsi's architecture like many other architectures, is divided into layers. It is "mainly" divided into two
            layers: The Data Layer & The Presentation Layer.

            The Data layer is responsible for performing network / local calls e.g fetching data from apis and the
            Presentation layer is responsible for performing presentation logic and and as a result show a piece of UI
            on the screen.
        </p>

        <g-image alt="Architecture diagram" src="~/assets/images/architecture.png" />

        <p>
            These two layers are further subdivided to their sub-layers:
            The Data layer is subdivided to the API and the Repository layers. The API layer will perform the
            network / local calls and return unstructured data e.g json. The sole responsibility of the Repository layer
            is to
            convert the unstructured data from the API layer to structured predefined data:- models.
        </p>

        <p>
            The Presentation layer is subdivided to State-Notifiers and Pages layer. Pages are mere UIs (widgets). But
            what UI is to be rendered on the screen is completely under the control of the state-notifiers. Hence the
            saying UI = f(state) holds true for this case.
        </p>

        <h2>2/4: Flow</h2>

        <g-image alt="Flow diagram" src="~/assets/images/flow.png" />

        <p>
            The first action will be triggered by the UI and then it's the state-notifier's job to emit specific states
            corresponding to different steps performed to complete that action.
        </p>

        <p>
            Code in state-notifier, repository & api layers is written with the SINGLE-RESPONSIBILITY principle in mind.
            Hence each function in classes in these layers has a unique purpose.
        </p>

        <p>
            A page can have access to (or listen to) multiple state notifiers, but each state-notifier only has access
            to a single repository, and each repository has access to a single API. This is also to obey SINGLE
            RESPONSIBILITY principle in a sense that each repository or state-notifier or api manages the activities of
            a single feature in case of (apis and repositories) and state(in case of state-notifiers). More about this
            in section 4: PAGES IN DETAIL
        </p>

        <p class="home-links">
            <a href="https://gridsome.org/docs/" target="_blank" rel="noopener">Gridsome Docs</a>
            <a href="https://github.com/gridsome/gridsome" target="_blank" rel="noopener">GitHub</a>
        </p>

    </Layout>
</template>

<script>
export default {
    metaInfo: {
        title: 'Hello, world!'
    }
}
</script>

<style>
.home-links a {
    margin-right: 1rem;
}
</style>
