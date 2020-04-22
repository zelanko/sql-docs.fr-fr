---
title: 'Étape 1 : Configurer un environnement pour Ruby'
description: Apprenez à configurer votre environnement de développement pour Ruby.
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8cdbadeb-f640-406c-977c-d2d44b7b5368
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 700b0c1979b0eccc1544afb59296fba867e24c53
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81634595"
---
# <a name="step-1-configure-development-environment-for-ruby-development"></a>Étape 1 : Configurer l’environnement de développement pour le développement Ruby
Vous devrez configurer votre environnement de développement avec les conditions préalables pour développer une application à l’aide du pilote Ruby pour SQL Server.    
  
Le pilote Ruby utilise le protocole TDS, qui est activé par défaut dans SQL Server et Azure SQL Database.  Aucune configuration supplémentaire n’est nécessaire.  
  
  
## <a name="windows"></a>Windows  
  
1.  **Télécharger le programme d'installation Ruby**  
Si votre ordinateur ne dispose pas de Ruby, installez-le. Pour les nouveaux utilisateurs de Ruby, nous vous recommandons d’utiliser les programmes d’installation Ruby 2.2.X, qui fournissent un langage stable et une liste complète de packages compatibles et mis à jour. Accédez à la [page de téléchargement Ruby](https://rubyinstaller.org/downloads/) et téléchargez le programme d’installation 2.1.x approprié. Par exemple, si vous êtes sur un ordinateur 64 bits, téléchargez le programme d’installation Ruby 2.1.6 (x64).   
  
2.  **Installer Ruby**  
Une fois le programme d’installation téléchargé :  
a. Pour démarrer le programme d'installation, double-cliquez sur le fichier.  
b. Sélectionnez votre langue et acceptez les termes du contrat.  
c.  Dans l’écran des paramètres d’installation, activez les cases à cocher Add Ruby executables to your PATH (Ajouter les exécutables Ruby à votre CHEMIN) et Associate .rb and .rbw files with this Ruby installation (Associer les fichiers `.rb` et `.rbw` avec cette installation de Ruby).  
  
3.  **Télécharger Ruby DevKit**  
Télécharger DevKit à partir de la page RubyInstaller  
  
4.  **Installer Ruby DevKit**  
Une fois le téléchargement terminé :  
a. Double-cliquez sur le fichier. Vous serez invité à indiquer l’emplacement d’extraction des fichiers.  
b. Cliquez sur le bouton « ... », puis sélectionnez « C:\DevKit ». Vous devrez probablement créer ce dossier pour la première fois en cliquant sur « Créer un nouveau dossier ».  
c. Cliquez sur « OK » puis sur « Extraire » pour extraire les fichiers.  
  
5. **Ouvrir cmd. exe**  
  
6. **Initialiser Ruby DevKit**  
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
  
1. **Ouvrir le terminal**  
  
2. **Installer Ruby Version Manager (`rvm`) et prérequis**  
```  
> sudo apt-get --assume-yes update  
> command curl -sSL https://rvm.io/mpapis.asc | gpg --import -  
> curl -L https://get.rvm.io | bash -s stable  
> source ~/.rvm/scripts/rvm  
```  
   
3. **Utiliser `rvm` pour installer Ruby**  
Par exemple, installez la version 2.3.0 de Ruby :  
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
  
5.  **Installer TinyTDS**  
```  
> gem install tiny_tds  
```  
  
## <a name="macos"></a>macOS  
  
Remarque : macOS dispose déjà de Ruby préinstallé, car le système d’exploitation a une dépendance.
  
1.  **Ouvrir le terminal**  
  
2. **Installer le gestionnaire de package Homebrew**  
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
