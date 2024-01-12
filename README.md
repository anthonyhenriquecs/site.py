# site.py
import flet as ft

def main(pagina):
    texto = ft.Text("Hashzap")
    
    nome_usuario = ft.TextField(label=("escreva seu nome:"))
    
    chat=ft.Column()
    
    
    
    def enviar_msg(evento):
        texto_campo_mensagem = f"{nome_usuario.value}: {campo_mensagem.value}"
        chat.controls.append((ft.Text(texto_campo_mensagem)))
        pagina.update()
        
    campo_mensagem = ft.TextField(label=("Digite sua mensagem:"), on_submit=enviar_msg)    
    botão_enviar = ft.ElevatedButton("Enviar",on_click=enviar_msg)
        
    def entrar_chat(evento):
        #fechar o popup
        pop_up.open=False
        #tire o botao iniciar da tela
        pagina.remove(boatao_iniciar)
        #Criar o chat
        pagina.add(chat)
        #criar o campo de enviar mensagem
        linha_mensagem = ft.Row(
            [campo_mensagem,botão_enviar]
        )
        pagina.add(linha_mensagem)
        #criar botao de enviar mensagem
        print(nome_usuario.value)
        pagina.update()
    
    pop_up = ft.AlertDialog(open=False,
                            modal=True,
                            title=ft.Text("HELLO"),
                            content=nome_usuario,
                            actions=[ft.ElevatedButton("ENTRAR", on_click=entrar_chat)])

    def iniciar_chat(evento):
        pagina.dialog = pop_up
        pop_up.open = True
        pagina.update()
        
    boatao_iniciar = ft.ElevatedButton("INICIAR", on_click=iniciar_chat)

    pagina.add(boatao_iniciar)
    pagina.add(texto)

ft.app(main)
