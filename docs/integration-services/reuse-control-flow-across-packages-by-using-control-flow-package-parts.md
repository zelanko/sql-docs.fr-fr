---
title: "R&#233;utiliser un flux de contr&#244;le sur des packages &#224; l’aide de composants de package de flux de contr&#244;le | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.toolboxcontrolflowtemplate.f1"
  - "sql13.dts.designer.addcopyexistingtemplate.f1"
  - "sql13.dts.designer.addcopyexistingpackagepart.f1"
  - "sql13.dts.designer.packagepart.general.f1"
ms.assetid: 1edc91d9-1fab-4fe5-aed3-6f581fe32c18
caps.latest.revision: 14
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 14
---
# R&#233;utiliser un flux de contr&#244;le sur des packages &#224; l’aide de composants de package de flux de contr&#244;le
  Enregistrez une tâche ou un conteneur de flux de contrôle couramment utilisés dans un fichier de pièce (fichier « .dtsxp ») autonome, et réutilisez celui-ci plusieurs fois dans un ou plusieurs packages à l’aide de composants de package de flux de contrôle. Cette réutilisation facilite la conception et la gestion des packages SSIS.  
  
## Créer un composant de package de flux de contrôle  
 Pour créer un composant de package de flux contrôle, dans l’Explorateur de solutions, développez le dossier **Package Parts** (Composants de package). Cliquez avec le bouton droit sur **Control Flow** (Flux de contrôle), puis sélectionnez **New Control Flow Package Part** (Nouveau composant de package de flux de contrôle).  
  
 ![Create a new control flow template](../integration-services/media/control-flow-templates-create-new.png "Create a new control flow template")  
  
 Un nouveau fichier de composant portant l’extension « .dtsxp » est créé dans le dossier **Package Parts | Control Flow** (Composants de Package | Flux de contrôle). En même temps, un nouvel élément du même nom est ajouté à la boîte à outils SSIS. (L’élément de boîte à outils est visible uniquement pendant que vous avez un projet contenant le composants ouvert dans Visual Studio.)  
  
 ![Control flow templates in toolbox](../integration-services/media/control-flow-templates-in-toolbox.png "Control flow templates in toolbox")  
  
## Concevoir un composant de package de flux de contrôle  
 Pour ouvrir l’éditeur de composant de package, double-cliquez sur le fichier du composant dans l’Explorateur de solutions. Vous pouvez concevoir le composant de la même manière qu’un package.  
  
 ![Step 1 of control flow template design](../integration-services/media/control-flow-template-design-step-1.png "Step 1 of control flow template design")  
  
 ![Step 2 of control flow template design](../integration-services/media/control-flow-template-design-step-2.png "Step 2 of control flow template design")  
  
 Vérifiez que les composants du flux de contrôle présentent les limitations suivantes.  
  
-   Un composant ne peut avoir qu’une seule tâche ou un seul conteneur de niveau supérieur. Si vous voulez inclure plusieurs tâches ou conteneurs, placez-les tous dans un conteneur de séquences unique.  
  
-   Vous ne pouvez pas exécuter ou déboguer un composant directement dans le concepteur.  
  
## Ajouter un composant de package de flux contrôle existant à un package  
 Vous pouvez réutiliser des composants enregistrés dans le projet Integration Services en cours ou dans un autre projet.  
  
-   Pour réutiliser un composant faisant partie du projet actuel, glissez-déplacez le composant à partir de la boîte à outils.  
  
-   Pour réutiliser un composant faisant partie d’un autre projet, utilisez la commande **Add Existing Control Flow Package Part** (Ajouter un composant de package de flux de contrôle existant).  
  
### Glisser-déplacer un composant de package de flux de contrôle  
 Pour réutiliser un composant dans un projet, glissez-déplacez simplement l’élément composant comme tout autre conteneur ou tâche à partir de la boîte à outils. Vous pouvez glisser-déplacer le composant vers un package plusieurs fois afin de réutiliser la logique en plusieurs emplacements du package. Recourez à cette méthode pour réutiliser un composant faisant partie du projet actuel.  
  
 ![Add a control flow template to a package](../integration-services/media/control-flow-templates-add-to-package.png "Add a control flow template to a package")  
  
 ![Package with multiple control flow templates](../integration-services/media/control-flow-templates-in-package.png "Package with multiple control flow templates")  
  
 Lorsque vous enregistrez le package, le concepteur SSIS vérifie s’il existe des instances du composant dans le package.  
  
-   Si le package contient des instances du composant, le concepteur génère un nouveau .dtsx.designer contenant toutes les informations relatives au composant.  
  
-   Si le package n’utilise pas de composant, le concepteur supprime tout fichier .dtsx.designer créé précédemment pour le package (autrement dit, tout fichier .dtsx.designer portant le même nom que le package).  
  
 ![Solution Explorer with control flow templates](../integration-services/media/control-flow-templates-in-solution-explorer.png "Solution Explorer with control flow templates")  
  
### Ajouter une copie d’un composant de package de flux contrôle existant ou une référence à un composant existant  
 Pour ajouter à un package une copie d’un composant existant dans le système de fichiers, dans l’Explorateur de solutions, développez le dossier **Package Parts** (Composants de package). Cliquez avec le bouton droit sur **Control Flow** (Flux de contrôle), puis sélectionnez **Add Existing Control Flow Package Part** (Ajouter un composant de package de flux de contrôle existant).  
  
 ![Add a new control flow templates from the menu](../integration-services/media/control-flow-templates-add-from-menu.png "Add a new control flow templates from the menu")  
  
 ![Add Copy of Existing Templates dialog box](../integration-services/media/control-flow-templates-add-copy-dialog.png "Add Copy of Existing Templates dialog box")  
  
 **Options**  
  
 **Chemin d’accès au composant de package**  
 Tapez le chemin de fichier du composant, ou cliquez sur le bouton Parcourir (...) pour localiser le fichier de composant à copier ou à référencer.  
  
 **Ajouter en tant que référence**  
 -   Si le composant est sélectionné, il est ajouté au projet Integration Services en tant que référence. Sélectionnez cette option si vous voulez référencer une copie unique d’un fichier de composant dans plusieurs projets Integration Services.  
  
-   Si cette option est désactivée, une copie du fichier du composant est ajoutée au projet.  
  
## Configurer un composant de package de flux de contrôle  
 Pour configurer des composants de package de flux de contrôle après les avoir ajoutés au flux de contrôle d’un package, utilisez la boîte de dialogue **Package Part Configuration**  (Configuration de composant de package).  
  
#### Pour ouvrir la boîte de dialogue Package Part Configuration (Configuration de composant de package)  
  
1.  Pour configurer une instance de composant, double-cliquez dessus dans le flux de contrôle. Vous pouvez également cliquer avec le bouton droit sur l’instance de composant, puis sélectionner **Modifier**. La boîte de dialogue **Package Part Configuration** (Configuration de composant de package).  
  
2.  Configurez les propriétés et les gestionnaires de connexion pour l’instance de composant.  
  
### Onglet Propriétés  
 Utilisez l’onglet **Properties** (Propriétés) de la boîte de dialogue **Package Part Configuration**  (Configuration de composant de package).  
  
 ![Properties tab of the Template Configuration dialog box](../integration-services/media/template-configuration-properties-tab.png "Properties tab of the Template Configuration dialog box")  
  
 La hiérarchie d’arborescence dans le volet gauche répertorie toutes les propriétés configurables de l’instance de composant.  
  
-   Si elle est désactivée, la propriété n’est pas configurée dans l’instance de composant. L’instance de composant utilise la valeur par défaut de la propriété, qui est définie dans le composant de package de flux de contrôle.  
  
-   Si elle est sélectionnée, la valeur que vous entrez ou sélectionnez remplace la valeur par défaut.  
  
 La table dans le volet droit répertorie les propriétés à configurer.  
  
-   **Property Path**(Chemin d’accès à la propriété). Chemin d’accès à la propriété.  
  
-   **Property Type**(Type de propriété). Type de données de la propriété.  
  
-   **Valeur**. Valeur configurée. Cette valeur remplace la valeur par défaut.  
  
### Onglet Connection Managers (Gestionnaires de connexions)  
 L’onglet **Connection Managers** (Gestionnaires de connexions) dans la boîte de dialogue **Package Part Configuration**  (Configuration de composant de package) permet de spécifier les propriétés des gestionnaires de connexions pour l’instance de composant.  
  
 ![Connection Managers tab of the Template Configuration dialog box](../integration-services/media/template-configuration-connection-managers-tab.png "Connection Managers tab of the Template Configuration dialog box")  
  
 Le tableau dans le volet gauche répertorie tous les gestionnaires de connexions définis dans le composant de flux de contrôle. Choisissez le gestionnaire de connexions à configurer.  
  
 La liste dans le volet droit répertorie les propriétés du gestionnaire de connexions sélectionné.  
  
-   **Set**(Définie). Option activée si la propriété est configurée pour l’instance de composant.  
  
-   **Property Name**(Nom de la propriété). Nom de la propriété.  
  
-   **Valeur**. Valeur configurée. Cette valeur remplace la valeur par défaut.  
  
## Supprimer un composant de flux de contrôle  
 Pour supprimer un composant, dans l’Explorateur de solutions, cliquez avec le bouton droit sur le composant, puis sélectionnez **Delete** (Supprimer). Sélectionnez **OK** pour confirmer la suppression, ou sélectionnez **Cancel** (Annuler) pour conserver le composant.  
  
 Si vous supprimez un composant d’un projet, il est supprimé définitivement du système de fichiers et ne peut pas être restauré.  
  
> [!NOTE]  
>  Si vous voulez supprimer un composant d’un projet Integration Services, mais continuer à l’utiliser dans d’autres projets, utilisez l’option **Exclude from Project** (Exclure du projet ) au lieu de l’option **Delete** (Supprimer).  
  
## Les composants de package sont des fonctionnalités disponibles uniquement au moment de la conception.  
 Les composants de package sont des fonctionnalités disponibles au moment du design caractéristiques. Le concepteur SSIS crée, ouvre, enregistre et met à jour des composants, et ajoute, configure ou supprime des instances de composant dans un package. En revanche, le runtime SSIS n’est pas informé de la présence de composants. Voici comment le concepteur accomplit cette séparation.  
  
-   Le concepteur enregistre les instances de composant de package avec leurs propriétés configurées pour un fichier « .dtsx.designer ».  
  
-   Lorsque le concepteur enregistre le fichier « .dtsx.designer », il extrait également le contenu des composants référencés par ce fichier et remplace les instances de composant dans le package par le contenu des composants.  
  
-   Enfin, tout le contenu, qui n’inclut plus d’informations sur le composant, est réenregistré dans le fichier de package « .dtsx ». Il s’agit du fichier que le runtime SSIS exécute.  
  
 Le diagramme ci-dessous illustre la relation entre les composants (fichiers « .dtsxp »), le concepteur SSIS et le runtime SSIS.  
  
 ![Control flow templates files and flow](../integration-services/media/control-flow-templates-intro.png "Control flow templates files and flow")  
  
  