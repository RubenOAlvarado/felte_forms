<script>
    import { createForm } from "felte";
    import { validator } from "@felte/validator-yup";
    import * as yup from "yup";
    import reporterDom from "@felte/reporter-dom";
    import Result from "./Result.svelte";
    import Input from "./Input.svelte";
    import Textarea from "./Textarea.svelte";

    const schema = yup.object({
        profile: yup.object({
            name: yup.string().required('El nombre es requerido'),
            email: yup.string().email('Debe ser un email').required('El email es requerido')
        }),
        details: yup.object({
            description: yup.string().optional()
        })
    });

    //objeto donde almacenaremos el resultado de nuestro formulario
    // y que después pasaremos como prop al componente result
    $: result = {
        profile: {
            name: '',
            email: ''
        },
        details:{
            description: ''
        }
    };

    //nuestra funcion recibe como parámetro los valores del formulario
    const onSubmit = (values) => {
        result = {...values};
    }

    const { form } = createForm({
        extend: [validator, reporterDom()],
        validateSchema: schema,
        onSubmit
    });
</script>

<div class="nes-container">
    <form use:form>
        <fieldset name="profile">
            <Input id="name" name="name" label="Nombre:" placeholder="Introduce el nombre:" />
            <Input id="email" name="email" label="Correo electrónico:" placeholder="Introduce el correo electrónico:" />
        </fieldset>
        <fieldset name="details">
            <Textarea id="description" name="description" label="Descripción:" placeholder="Introduce una descripción(opcional)." />
        </fieldset>
        <input type="submit" class="nes-btn is-primary" value="Guardar" />
        <button type="reset" class="nes-btn is-error">Cancelar</button>
    </form>
</div>

{#if result.profile.name}
    <Result bind:result />
{/if}