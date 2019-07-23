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
ms.openlocfilehash: 38af92d3cb0354bc4b75131a349f6a1c26e90490
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67992458"
---
# <a name="step-1-configure-development-environment-for-ruby-development"></a>Étape 1 : Configurer l’environnement de développement pour le développement Ruby
Vous devrez configurer votre environnement de développement avec les conditions préalables pour développer une application à l’aide du pilote Ruby pour SQL Server.    
  
Notez que le pilote Ruby utilise le protocole TDS, qui est activé par défaut dans SQL Server et Azure SQL Database.  Aucune configuration supplémentaire n’est requise.  
  
  
## <a name="windows"></a>Windows  
  
1.  **Télécharger Ruby installer**  
Si votre ordinateur ne dispose pas de Ruby, installez-le. Pour les nouveaux utilisateurs de Ruby, nous vous recommandons d’utiliser des programmes d’installation Ruby 2.2. X. Ils fournissent un langage stable et une liste complète des packages compatibles et mis à jour. Accédez à la [page de téléchargement Ruby](https://rubyinstaller.org/downloads/) et téléchargez le programme d’installation 2.1. x approprié. Par exemple, si vous êtes sur un ordinateur 64 bits, téléchargez le programme d’installation Ruby 2.1.6 (x64).   
  
2.  **Installer ruby**  
Une fois le programme d’installation téléchargé, procédez comme suit:  
A. Double-cliquez sur le fichier pour démarrer le programme d’installation.  
B. Sélectionnez votre langue et acceptez les termes du contrat.  
c.  Dans l’écran Paramètres d’installation, activez les cases à cocher en regard de ajouter des exécutables Ruby à vos fichiers PATH et Associate. RB et. RBW avec cette installation Ruby.  
  
3.  **Télécharger Ruby DevKit**  
Télécharger DevKit à partir de la page RubyInstaller  
  
4.  **Installer ruby DevKit**  
Une fois le téléchargement terminé, procédez comme suit:  
A. Double-cliquez sur le fichier. Vous serez invité à indiquer l’emplacement d’extraction des fichiers.  
B. Cliquez sur le «...» et sélectionnez «C:\DevKit». Vous devrez probablement créer ce dossier pour la première fois en cliquant sur «créer un nouveau dossier».  
c. Cliquez sur «OK», puis sur «extraire» pour extraire les fichiers.  
  
5. **Ouvrez cmd. exe**  
  
6. **Initialiser Ruby DevKit**  
```  
> chdir C:\DevKit  
> ruby dk.rb init  
> ruby dk.rb install  
```  
  
7.  **Installer la gemme fonction tinytds**  
```  
> gem inst tiny_tds
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1. **Ouvrir le terminal**  
  
2. **Installer ruby version Manager (RVM) et conditions préalables**  
```  
> sudo apt-get --assume-yes update  
> command curl -sSL https://rvm.io/mpapis.asc | gpg --import -  
> curl -L https://get.rvm.io | bash -s stable  
> source ~/.rvm/scripts/rvm  
```  
   
3. **Utiliser RVM pour installer Ruby**  
Par exemple, installez la version 2.3.0 de Ruby:  
```  
> rvm install 2.3.0  
> rvm use 2.3.0 --default  
> ruby -v  
```  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Vérifiez que la sortie de la dernière commande indique que vous exécutez la version 2.3.0.  
  
4.  **Installer FreeTDS**  
```  
> sudo apt-get --assume-yes install freetds-dev freetds-bin  
```  
  
5.  **Installer fonction tinytds**  
```  
> gem install tiny_tds  
```  
  
## <a name="mac"></a>Mac  
  
Notez que Mac OS X dispose déjà de Ruby préinstallé, car le système d’exploitation a une dépendance.    
  
1.  **Ouvrir le terminal**  
  
2. **Installer le gestionnaire de package homebrew**  
```  
> ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"  
```  
  
3.  **Installer FreeTDS**  
```  
> brew install FreeTDS  
```  
  
4.  **Installer la gemme fonction tinytds**  
```  
> gem install tiny_tds  
```
