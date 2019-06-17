---
title: 'Étape 1 : Configurer l’environnement de développement pour le développement Ruby | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8cdbadeb-f640-406c-977c-d2d44b7b5368
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: ff03ce6ec79aede2e056f0154836e77970af9c50
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66800833"
---
# <a name="step-1-configure-development-environment-for-ruby-development"></a>Étape 1 : Configurer l’environnement de développement pour le développement Ruby
Vous devez configurer votre environnement de développement avec la configuration requise pour développer une application en utilisant le pilote Ruby pour SQL Server.    
  
Notez que le pilote Ruby utilise le protocole TDS, qui est activé par défaut dans SQL Server et de la base de données SQL Azure.  Aucune configuration supplémentaire n’est requise.  
  
  
## <a name="windows"></a>Windows  
  
1.  **Télécharger le programme d’installation de Ruby**  
Si votre ordinateur ne dispose pas de Ruby installez-la. Pour les nouveaux utilisateurs ruby, nous vous recommandons de qu'utiliser les programmes d’installation de Ruby 2.2.X. Ils fournissent un langage stable et une liste complète des packages (perles) qui sont compatibles et mis à jour. Atteindre le [page de téléchargement Ruby](https://rubyinstaller.org/downloads/) et téléchargez le programme d’installation 2.1.x approprié. Par exemple, si vous êtes sur un ordinateur 64 bits, téléchargez le programme d’installation Ruby 2.1.6 (x64).   
  
2.  **Installez Ruby**  
Une fois le programme d’installation est téléchargé, procédez comme suit :  
A. Double-cliquez sur le fichier pour démarrer le programme d’installation.  
B. Sélectionnez votre langue, puis acceptez les termes du contrat.  
c.  Dans l’écran de paramètres d’installation, sélectionnez les cases à cocher en regard de ces deux exécutables Ruby ajouter à vos fichiers .rb et .rbw chemin d’accès et l’associer avec cette installation de Ruby.  
  
3.  **Télécharger le Kit de développement Ruby**  
Télécharger le Kit de développement à partir de la page RubyInstaller  
  
4.  **Installer le Kit de développement Ruby**  
Une fois le téléchargement est terminé, procédez comme suit :  
A. Double-cliquez sur le fichier. Nous vous demanderons de laquelle extraire les fichiers.  
B. Cliquez sur le bouton «... », puis sélectionnez « C:\DevKit ». Vous devrez probablement d’abord créer ce dossier en cliquant sur « Créer un nouveau dossier ».  
c. Cliquez sur « OK », puis « extraire, » pour extraire les fichiers.  
  
5. **Ouvrez cmd.exe**  
  
6. **Initialiser le Kit de développement Ruby**  
```  
> chdir C:\DevKit  
> ruby dk.rb init  
> ruby dk.rb install  
```  
  
7.  **Installer TinyTDS gem**  
```  
> gem inst tiny_tds
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1. **Ouvrir terminal**  
  
2. **Installez Ruby Version Manager (rvm) et les composants requis**  
```  
> sudo apt-get --assume-yes update  
> command curl -sSL https://rvm.io/mpapis.asc | gpg --import -  
> curl -L https://get.rvm.io | bash -s stable  
> source ~/.rvm/scripts/rvm  
```  
   
3. **Rvm permet d’installer Ruby**  
Par exemple, installez la version 2.3.0 de Ruby :  
```  
> rvm install 2.3.0  
> rvm use 2.3.0 --default  
> ruby -v  
```  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Vérifiez que la sortie de la dernière commande indique la que version 2.3.0 sont en cours d’exécution.  
  
4.  **Installer FreeTDS**  
```  
> sudo apt-get --assume-yes install freetds-dev freetds-bin  
```  
  
5.  **Installer TinyTDS**  
```  
> gem install tiny_tds  
```  
  
## <a name="mac"></a>Mac  
  
Notez que Mac OS X prend déjà en Ruby préinstallé, comme le système d’exploitation a une dépendance.    
  
1.  **Ouvrir terminal**  
  
2. **Installer le Gestionnaire de package Homebrew**  
```  
> ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"  
```  
  
3.  **Installer FreeTDS**  
```  
> brew install FreeTDS  
```  
  
4.  **Installer TinyTDS gem**  
```  
> gem install tiny_tds  
```
