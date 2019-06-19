---
title: 'Étape 2 : Activer et définir les configurations du package | Microsoft Docs'
ms.custom: ''
ms.date: 01/08/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 005218ab-8dd5-48e9-a185-6bc60cd43a7a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ee2c54b072cf9cd219bed10b0ade7f59fa8bc354
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65721523"
---
# <a name="lesson-5-2-enable-and-configure-package-configurations"></a>Leçon 5-2 : Activer et définir les configurations du package

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



Au cours de cette tâche, vous convertissez le projet en modèle de déploiement de package et activez les configurations du package à l’aide de l’Assistant Configuration de package. Vous utilisez cet Assistant pour générer un fichier de configuration XML qui contient les paramètres de configuration de la propriété **Directory** du conteneur de boucles Foreach. La valeur de la propriété **Directory** est fournie par une nouvelle variable de niveau package que vous pouvez mettre à jour au moment de l’exécution. Vous remplissez également un dossier New Sample Data à utiliser pour le test.  
  
## <a name="create-a-package-level-variable-mapped-to-the-directory-property"></a>Créer une variable de niveau package mappée à la propriété Directory  
  
1.  Sélectionnez l’arrière-plan de l’onglet **Flux de contrôle** dans le Concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)]. Cette sélection permet de définir l’étendue de la variable que vous créez pour le package.  
  
2.  Dans le menu [!INCLUDE[ssIS](../includes/ssis-md.md)] , cliquez sur **Variables**.  
  
3.  Dans la fenêtre **Variables**, sélectionnez l’icône **Ajouter une variable**.  
  
4.  Dans la zone **Nom**, entrez **varFolderName**.  
  
    > [!IMPORTANT]  
    > Les noms de variable respectent la casse.  
  
5.  Vérifiez que la zone **Étendue** affiche le nom du package de la leçon 5 (**Lesson 5**).  
  
6.  Définissez la valeur de la zone **Type de données** de la variable `varFolderName` à **String**.  
  
7.  Réaffichez l’onglet **Flux de contrôle** et double-cliquez sur le conteneur **Foreach File in Folder** .  
  
8.  Dans la page **Collection** de l’**Éditeur de boucle Foreach**, sélectionnez **Expressions**, puis le bouton de sélection **(...)** .  
  
9. Dans l’**Éditeur d’expressions de la propriété**, sélectionnez la liste **Propriété**, puis **Directory**.  
  
10. Dans la zone **Expression**, sélectionnez le bouton de sélection **(...)** .  
  
11. Dans le **Générateur d’expressions**, développez le dossier **Variables et paramètres** et faites glisser la variable **User::varFolderName** vers la zone **Expression**.  
  
12. Sélectionnez **OK** pour quitter le **Générateur d’expressions**.  
  
13. Sélectionnez **OK** pour quitter l’**Éditeur d’expressions de la propriété**.  
  
14. Sélectionnez **OK** pour quitter l’**Éditeur de boucle Foreach**.  
  
## <a name="enable-package-configurations"></a>Activer les configurations du package  
  
1.  Dans le **menu Projet**, sélectionnez **Convertir en modèle de déploiement de package**.  
  
2.  Sélectionnez **OK** dans l’invite d’avertissement et, une fois la conversion terminée, sélectionnez **OK** dans la boîte de dialogue **Convertir en modèle de déploiement de package**.  
  
3.  Sélectionnez l’arrière-plan de l’onglet **Flux de contrôle** dans le Concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)].  
  
4.  Dans le menu **SSIS**, sélectionnez **Configurations du package**.  
  
5.  Dans la boîte de dialogue **Bibliothèque des configurations du package**, sélectionnez **Activer les configurations du package**, puis **Ajouter**.  
  
6.  Dans la page d’accueil de l’**Assistant Configuration de package**, sélectionnez **Suivant**.  
  
7.  Dans la page **Sélectionner le type de configuration** , vérifiez que **Type de configuration** a la valeur **Fichier de configuration XML**.  
  
8.  Dans la page **Sélectionner le type de configuration**, sélectionnez **Parcourir**.  
  
9. La boîte de dialogue **Sélectionner l’emplacement du fichier de configuration** s’ouvre et contient le dossier du projet.  
  
10. Dans la boîte de dialogue **Sélectionner l’emplacement du fichier de configuration**, entrez **SSISTutorial** dans la zone **Nom de fichier**, puis sélectionnez **Enregistrer**.  
  
11. Dans la page **Sélectionner le type de configuration**, sélectionnez **Suivant**.
  
12. Dans la page **Sélectionner les propriétés à exporter**, dans le volet **Objets**, développez **Variables**, **varFolderName**, **Propriétés**, puis sélectionnez **Valeur**.  
  
13. Dans la page **Sélectionner les propriétés à exporter**, sélectionnez **Suivant**.  
  
14. Dans la page **Fin de l’Assistant**, entrez un nom de configuration, par exemple **Configuration du répertoire du tutoriel SSIS**. Le nom de configuration s’affiche dans la boîte de dialogue **Bibliothèque des configurations du package**.  
  
15. Sélectionnez **Terminer**.  
  
16. Sélectionnez **Fermer**.  
  
17. L’Assistant crée un fichier de configuration appelé **SSISTutorial.dtsConfig**, qui contient les paramètres de configuration pour la valeur (**Value**) de la variable, qui définit à son tour la propriété **Directory** de l’énumérateur.  
  
    > [!NOTE]  
    > Un fichier de configuration contient généralement des informations complexes sur les propriétés de package mais, dans le cadre de ce tutoriel, la seule information qui nous concerne doit se présenter comme suit :

    ```
    <Configuration 
        ConfiguredType="Property"  
        Path="\Package.Variables[User::varFolderName].Properties[Value]" 
        ValueType="String">  
      <ConfiguredValue></ConfiguredValue>  
    </Configuration>
    ```
  
## <a name="create-and-populate-a-new-sample-data-folder"></a>Créer et remplir un dossier New Sample Data  
  
1.  Dans l’Explorateur Windows, à la racine de votre lecteur (par exemple, **C:\\** ), créez un dossier appelé **New Sample Data**.  
  
2.  Localisez les fichiers d'exemple sur votre ordinateur et copiez trois des fichiers du dossier.  
  
3.  Dans le dossier **New Sample Data** , collez les fichiers que vous venez de copier.  
  
## <a name="go-to-next-task"></a>Passer à la tâche suivante  
[Étape 3 : Modifier la valeur de configuration de la propriété Directory](../integration-services/lesson-5-3-modifying-the-directory-property-configuration-value.md)  
  
