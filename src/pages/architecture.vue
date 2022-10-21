<template>
    <Layout>

        <h1>ARCHITECTURE / SOFTWARE DESIGN</h1>

        <h2>1/3: Architecture layers</h2>

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

        <h2>2/3: Flow</h2>

        <g-image alt="Flow diagram" src="~/assets/images/flow.png" />

        <p>
            The first action will be triggered by the UI and then it's the state-notifier's job to emit specific states
            corresponding to different steps performed to complete that action.
        </p>

        <p>
            Coming from the repositories are either models or exceptions, it depends on the server response. Both of
            these are structured & pre-defined and take part in "what-state-to-emit-next" decisions by the
            state-notifiers.
        </p>

        <p>
            Code in state-notifier, repository & api layers is written with the SINGLE-RESPONSIBILITY principle in mind.
            Hence each function in classes in these layers has a unique purpose.
        </p>

        <p>
            A page can have access to (or listen to) multiple state notifiers, but each state-notifier only has access
            to a single repository, and each repository has access to a single API. This is also to obey SINGLE
            RESPONSIBILITY principle in a sense that each repository or state-notifier or api manages the activities of
            a single feature in case of (apis and repositories) and state(in case of state-notifiers).
        </p>

        <h2>3/3: Folder & Files Organization</h2>

        <g-image alt="Folder & Files Organization" src="~/assets/images/files-and-folders-org.png" width="877.2"
            height="661.3" fit="contain" />

        <p>
            As it is seen, the architecture itself is more of a layer-first as opposed to feature-first.
        </p>

        <h1>PAGES IN DETAIL</h1>

        <p>
            This section is more about the interactions of pages in the code, and to clarify what was written in the
            last
            paragraph of the second section.
        </p>

        <g-image alt="Flow diagram" src="~/assets/images/page.png" />

        <h2>1/2 Value-Notifiers vs State-Notifiers</h2>

        <p>
            Value notifiers are used to preserve the state of certain widgets in the page before sending complete
            required data to the state-notifiers when a certain action is to be done. Value-notifiers have come into
            action to avoid maintain the state of
            widgets in the state notifiers. State notifiers will only be used in activities like logIn, signUp etc which
            most of the time will require sending data to the server and getting a response back. Hence activities like
            validating login or sign-up inputs or making sure that the
            T·O·C checkbox is checked or similar issues are completely handled by the value notifiers.
        </p>

        <g-image alt="Flow diagram" src="~/assets/images/sample-uis.png" />

        <p>
            In the picture above are sample Registration & Post upload UIs. These UIs are used as an attempt to
            demonstrate what sorts of activities will be handled by the value-notifiers and what activities by
            state-notifiers.
        </p>

        <p>
            In the registration UI, all validation activities here are to be handled by the page itself before sending
            email and password to the state-notifier. Managing state in the widgets is mostly done in the app by
            value-notifiers. This makes it easy to understand the logic in the state-notifiers. Code in the
            state-notifier could be something like this:
        </p>

        <g-image alt="Flow diagram" src="~/assets/images/registration-code.png" width="700" />

        <p>
            In the post UI, all validation activities e.g. if caption is added (if that's required) or maintaining the
            state of whether the location or tag buttons are tapped is all handled by the pages themeselves
            and not state-notifiers. Code in the state-notifier could be like:
        </p>

        <g-image alt="Flow diagram" src="~/assets/images/upload-code.png" width="600" />

        <h2>2/2 State listeners</h2>

        <p>
            State listeners have been used throughout the app for step-by-step processes. Consider the registration
            process: It might go through 4 processes for it to be considered complete.
        </p>

        <g-image alt="Flow diagram" src="~/assets/images/registration.png" />

        <p>
            Code below shows one way that could be accomplished.
        </p>

        <g-image alt="Flow diagram" src="~/assets/images/registration-code-2.png" width="700" />

        <p>
            Code below shows one way that could be accomplished.
        </p>

        <g-image alt="Flow diagram" src="~/assets/images/listener-1.png" width="600"/>

        <g-image alt="Flow diagram" src="~/assets/images/listener-2.png" width="700" />

        <p class="home-links">
            <a href="https://gridsome.org/docs/" target="_blank" rel="noopener">Gridsome Docs</a>
            <a href="https://github.com/gridsome/gridsome" target="_blank" rel="noopener">GitHub</a>
        </p>

    </Layout>
</template>

<script>
export default {
    metaInfo: {
        title: 'ARCHITECTURE'
    }
}
</script>

<style>
.home-links a {
    margin-right: 1rem;
}
</style>
