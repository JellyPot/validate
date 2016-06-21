# Plugin pro validaci formul��� pomoc� JS

Sta�� p�ipojit skript do str�nky a zavolat funkci `validate()` na jQuery objekt formul��e. T��dy s v�sledkem validace jsou p�id�lov�ny automaticky rodi�i input pole.

## P��klad

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
                <span class="caption">Jm�no</span>
                <f:input runat="server" class="va vaS" id="name" validateas="NotEmpty" targetField="name" />
                <p class="msg">Jm�no je povinn�.</p>
            </label>
            <label>
                <span class="caption">Email</span>
                <f:input runat="server" class="va vaE" id="email" validateas="Email" targetField="email" />
                <p class="msg">Email je povinn�.</p>
            </label>
            <label>
                <span class="caption">Telefon</span>
                <f:input runat="server" class="va vaT vaAE" id="phone" validateas="NotEmpty" placeholder="" targetField="phone" />
                <p class="msg">Telefonn� ��slo je zad�no nespr�vn�.</p>
            </label>
        </formTemplate>
        <sentTemplate>
            <p>Odesl�no!</p>
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