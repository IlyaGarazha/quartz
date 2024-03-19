# Регистрация
![[Pasted image 20231122104248.png]]

Далее можете пропустить персонализацию (skip personalization)
# Создание репозитория

Перейдите теперь на https://github.com/. В правом верхнем углу выберите "Your profille"
![[Pasted image 20231122124155.png]]


![[Pasted image 20231122123725.png]]

Создайте приватный репозиторий с названием `Semester_2`

![[Pasted image 20231122124543.png]]

# Добавление участников

Перейдите в Settings ->  Collaborators -> Add People -> garazha-ilya
![[Pasted image 20231122133620.png]]

# Создание SSH-ключа

Для добавления SSH-ключа можно воспользоваться [интсрукцией](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent?platform=windows):
1. В командной строке введите
````shell
ssh-keygen -t ed25519 -C "your_email@example.com"
````

И можете 3 раза подряд нажать `Enter`
Для добавления ssh-ключа к ssh-клиенту необходимо

*Для Windows*:
Запустите PowerShell от *имени администратора*! и введите следующие команды:
```powershell
Get-Service -Name ssh-agent | Set-Service -StartupType Manual
```
```powershell
Start-Service ssh-agent
```
А затем в обычном терминале выполните
```powershell
ssh-add /c/Users/ВАШЕ_ИМЯ_ПОЛЬЗОВАТЕЛЯ/.ssh/id_ed25519
```
Для Linux:
```shell
eval "$(ssh-agent -s)"
```

```shell
ssh-add ~/.ssh/id_ed25519
```

![[Pasted image 20231122130657.png]]
Теперь откройте файл `id_ed25519.pub`

![[Pasted image 20231122131402.png]]
И скопируйте его содержимое в поле `key` на GitHub в разделе SSH and GPG keys -> New SSH key:

![[Pasted image 20231122125102.png]]

![[Pasted image 20231122125346.png]]

# Содержимое репозитория
## Клонирование:
![[Pasted image 20231122125618.png]]

На своём компьютере создаёте папку, в которую вы склонируете репозиторий (то, что скопировали на прошлом шаге `git@github.com:ВАШ_РЕПОЗИТОРИЙ`)
`git clone ...` 

![[Pasted image 20231122130431.png]]

Распакуйте [архив](https://drive.google.com/file/d/1lXZ8klLkiKUdpUtfKwnPxvJRGwmZ2dvm/view?usp=sharing) и добавьте все файлы `git add -A`, а затем создайте коммит и выполните `git push`

![[Pasted image 20231122132639.png]]

Добавьте SSH-ссылку на ваш репозиторий в [таблицу](https://docs.google.com/spreadsheets/d/1-z5g3qONlWRbUw1o7h92xSSIezMLCQ-N9SXuvzgX3FQ/edit#gid=493963240).