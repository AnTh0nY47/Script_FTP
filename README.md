# Script de Téléchargement FTP avec Notification par Email

## Description

Ce script PowerShell permet de télécharger un fichier depuis un serveur FTP et de notifier l'administrateur par email du succès ou de l'échec de l'opération. Il est conçu pour être utilisé dans des environnements Windows où PowerShell est disponible.

### Fonctionnalités :
- Connexion à un serveur FTP avec authentification par nom d'utilisateur et mot de passe.
- Téléchargement d'un fichier distant vers un emplacement local.
- Enregistrement d'un journal détaillant l'exécution du script (réussites et erreurs).
- Envoi d'une notification par email à un administrateur pour signaler le succès ou l'échec du téléchargement.

---

## Prérequis

1. PowerShell installé sur la machine exécutant le script.
2. Un accès au serveur FTP avec les informations d'identification nécessaires.
3. Un serveur SMTP configuré pour l'envoi d'emails (par exemple, Gmail).
4. Les ports nécessaires ouverts pour l'accès FTP et SMTP.

---

## Paramètres de Configuration

Avant d'exécuter le script, vous devez configurer certains paramètres selon votre environnement. Ces paramètres sont définis au début du script et incluent :

- **$FtpServer** : Adresse du serveur FTP (ex : "172.20.198.167").
- **$FtpUsername** : Nom d'utilisateur FTP.
- **$FtpPassword** : Mot de passe FTP.
- **$RemoteFilePath** : Chemin du fichier distant sur le serveur FTP (ex : "/home/anthony2/ftp/upload/var.tar.gz").
- **$LocalFilePath** : Chemin où le fichier sera enregistré localement (ex : "C:\Archives\var.tar.gz").
- **$AdminEmail** : Email de l'administrateur qui recevra les notifications (ex : "anth.boudet2@gmail.com").
- **$SmtpServer** : Serveur SMTP pour l'envoi des notifications (ex : "smtp.gmail.com").
- **$SmtpPort** : Port SMTP (souvent 587 ou 465).
- **$SmtpUser** : Utilisateur pour l'authentification SMTP.
- **$SmtpPassword** : Mot de passe pour l'authentification SMTP.

---

## Fonctionnement

Le script fonctionne en 4 étapes principales :

1. **Connexion FTP** : Le script tente de se connecter au serveur FTP avec les informations d'identification fournies et télécharge le fichier spécifié depuis le chemin distant vers le chemin local.
2. **Journalisation** : Chaque étape est enregistrée dans un fichier journal (logs), indiquant si le téléchargement a réussi ou échoué.
3. **Notification par Email** : Après l'exécution du script, une notification par email est envoyée à l'administrateur pour l'informer du succès ou de l'échec de l'opération.
4. **Gestion des Erreurs** : En cas d'erreur (connexion FTP ou envoi de l'email), un message d'erreur détaillé est inclus dans le corps de l'email, ainsi que dans le fichier journal.

---

## Exemple de sortie de journal

```
[2024-12-16 10:00:00] Script démarré. Les logs sont enregistrés dans C:\Logs\FtpDownloadLog_20241216_100000.log
[2024-12-16 10:00:10] Tentative de téléchargement du fichier depuis ftp://anthony2:azerty@172.20.198.167/home/anthony2/ftp/upload/var.tar.gz...
[2024-12-16 10:00:20] Téléchargement réussi depuis ftp://anthony2:azerty@172.20.198.167/home/anthony2/ftp/upload/var.tar.gz. Fichier enregistré à C:\Archives\var.tar.gz
[2024-12-16 10:00:30] Email envoyé avec succès à anth.boudet2@gmail.com
```

---

## Comment Exécuter le Script

1. Ouvrir PowerShell avec les privilèges administratifs.
2. Télécharger le fichier du script sur votre machine.
3. Modifier les paramètres de configuration (voir la section "Paramètres de Configuration").
4. Exécuter le script en tapant la commande suivante dans PowerShell :
   ```powershell
   .\script_name.ps1
   ```

---

## Sécurité

- **Ne jamais partager** vos informations d'identification FTP ou SMTP dans un fichier non sécurisé.
- Assurez-vous que les permissions sur les fichiers de log sont appropriées pour éviter les fuites d'informations sensibles.

---

## Conclusion

Ce script est un outil simple et efficace pour automatiser le processus de téléchargement FTP tout en fournissant une notification en cas de succès ou d'échec. Vous pouvez l'adapter à vos besoins spécifiques en fonction des serveurs et des chemins utilisés dans votre environnement.
