<script>
    import { onMount } from "svelte";

    let name = "";
    let email = "";
    let subject = "";
    let message = "";

    const handleSubmit = async (event) => {
        event.preventDefault();

        const formData = {
            name,
            email,
            subject,
            message,
        };

        try {
            const response = await fetch("/api/submitForm", {
                method: "POST",
                headers: {
                    "Content-Type": "application/json",
                },
                body: JSON.stringify(formData),
            });

            if (response.ok) {
                const result = await response.json();
                console.log(result.message); // Log success message
                // You can add code here to show a success message to the user
            } else {
                throw new Error("Form submission failed.");
            }
        } catch (error) {
            console.error("Error:", error);
            // Handle error, show error message to the user, etc.
        }
    };
</script>

<!--==================== CONTACT FORM ====================-->
<form on:submit={handleSubmit}>
    <label for="name">Naam</label>
    <input
        class="field"
        bind:value={name}
        type="text"
        id="name"
        name="name"
        required
    />

    <label for="email">E-mail</label>
    <input
        class="field"
        bind:value={email}
        type="email"
        id="email"
        name="email"
        required
    />

    <label for="subject">Onderwerp</label>
    <input
        class="field"
        bind:value={subject}
        type="text"
        id="subject"
        name="subject"
        required
    />

    <label for="message">Bericht</label>
    <textarea
        class="field"
        bind:value={message}
        id="message"
        name="message"
        rows="10"
        required
    />

    <input class="green-link no-border" type="submit" value="Versturen" />
</form>

<style>
    form {
        width: 100%;
    }

    .field {
        width: 100%;
        border: 1px solid #c2c2c2;
        padding: 0.4rem 0.5rem;
        border-radius: 0.5rem;
        margin: 0.5rem 0rem 1rem 0rem;
    }

    .no-border {
        border: none;
        color: white;
        text-decoration: none;
        cursor: pointer;
    }

    label {
        color: var(--darkblue);
    }

    textarea {
        resize: none;
    }

    textarea:focus,
    input:focus {
        outline-color: var(--green);
        outline-width: 1px;
    }
</style>
