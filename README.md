# site.py

import flet as ft
def main(pagina):
    texto = ft.Text("Hashzap")
    nome_usuario = ft.TextField(label=("escreva seu nome:"))
    pop_up = ft.AlertDialog(open=False,
                            modal=True,
                            title=ft.Text("HELLO"),
                            content=nome_usuario,
                            actions=[ft.ElevatedButton("ENTRAR")])

    def iniciar_chat(evento):
        pagina.dialog = pop_up
        pop_up.open = True
        pagina.update()
        
    boatao_iniciar = ft.ElevatedButton("INICIAR", on_click=iniciar_chat)

    pagina.add(boatao_iniciar)
    pagina.add(texto)

ft.app(main)
