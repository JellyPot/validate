# Plugin pro validaci formuláøù pomocí JS

Staèí pøipojit skript do stránky a zavolat funkci `validate()` na jQuery objekt formuláøe. Tøídy s výsledkem validace jsou pøidìlovány automaticky rodièi input pole.

## Pøíklad

*.aspx

```html
...
<script>
    $(function () {
        $('form').validate()
    })
</script>
...
<form method="post" runat="server">
    <f:EmailForm runat="server" id="comment" targetCollection=".comment" emailTemplate="Comment/sent">
        <formTemplate>
            <label>
                <span class="caption">Jméno</span>
                <f:input runat="server" class="va vaS" id="name" validateas="NotEmpty" targetField="name" />
                <p class="msg">Jméno je povinné.</p>
            </label>
            <label>
                <span class="caption">Email</span>
                <f:input runat="server" class="va vaE" id="email" validateas="Email" targetField="email" />
                <p class="msg">Email je povinný.</p>
            </label>
            <label>
                <span class="caption">Telefon</span>
                <f:input runat="server" class="va vaT vaAE" id="phone" validateas="NotEmpty" placeholder="" targetField="phone" />
                <p class="msg">Telefonní èíslo je zadáno nesprávnì.</p>
            </label>
        </formTemplate>
        <sentTemplate>
            <p>Odesláno!</p>
        </sentTemplate>
    </f:EmailForm>
</form>
...
```

*.sass

```sass
form {
    label {
        .msg {
            display: none;
        }
        &.error {
            input, textarea {
                border-color: orange;
                background-color: mix(orange, white, 10%);
            }
            .msg {
                color: orange;
                display: block;
            }
        }
        &.correct {
            input, textarea {
                border-color: green;
            }
        }
    }
}
```