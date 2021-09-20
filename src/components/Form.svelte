<script>
    import { createForm } from "felte";
    import { validator } from "@felte/validator-yup";
    import * as yup from "yup";
    import reporterDom from "@felte/reporter-dom";

    const { form } = createForm({
        extend: [validator, reporterDom()],
    });
</script>

<div class="nes-container">
    <form use:form />
</div>
