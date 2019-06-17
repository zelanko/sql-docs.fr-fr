---
title: 'Analysis Services leçon du didacticiel 1 : Créez un projet de modèle tabulaire | Microsoft Docs'
ms.date: 03/08/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 52e0b3f317044e25b2004512083fdcaff7a77ecf
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148984"
---
# <a name="create-a-tabular-model-project"></a>Créer un projet de modèle tabulaire

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

Dans cette leçon, vous utilisez Visual Studio avec SQL Server Data Tools (SSDT) ou Visual Studio 2017 avec Microsoft Analysis Services projets VSIX pour créer un nouveau projet de modèle tabulaire au niveau de compatibilité 1400. Une fois votre nouveau projet est créé, vous pouvez commencer l’ajout de données et de création de votre modèle. Cette leçon vous présente brièvement le modèle tabulaire, environnement de création dans Visual Studio.  
  
Durée estimée pour effectuer cette leçon : **10 minutes**  
  
## <a name="prerequisites"></a>Prérequis

Cet article est la première leçon du didacticiel de conception de modèle tabulaire. Pour suivre cette leçon, il existe plusieurs conditions préalables que doivent être satisfaites. Pour plus d’informations, consultez [Analysis Services - didacticiel Adventure Works](../tutorial-tabular-1400/as-adventure-works-tutorial.md).  
  
## <a name="create-a-new-tabular-model-project"></a>Créer un projet de modèle tabulaire  
  
#### <a name="to-create-a-new-tabular-model-project"></a>Pour créer un projet de modèle tabulaire  
  
1.  Dans Visual Studio, sur le **fichier** menu, cliquez sur **New** > **projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue, développez **installé** > **Business Intelligence** > **Analysis Services**, puis cliquez sur **projet tabulaire Analysis Services**.  
  
3.  Dans **nom**, type **AW Internet Sales**, puis spécifiez un emplacement pour les fichiers de projet.  
  
    Par défaut, **nom de la Solution** est le même que le nom du projet ; Toutefois, vous pouvez taper un nom de solution différent.  
  
4.  Cliquez sur **OK**.  
  
5.  Dans le **Générateur de modèles tabulaires** boîte de dialogue, sélectionnez **espace de travail intégré**.  
  
    L’espace de travail héberge une base de données de modèle tabulaire portant le même nom que le projet lors de la création de modèles. Espace de travail intégré signifie que Visual Studio utilise une instance intégrée, éliminant le besoin d’installer une instance de serveur Analysis Services distincte uniquement pour la création du modèle.
      
6.  Dans **niveau de compatibilité**, sélectionnez **SQL Server 2017 / Azure Analysis Services (1400)** .   
 
    ![as-lesson1-tmd](../tutorial-tabular-1400/media/as-lesson1-tmd.png)
      
    Si vous ne voyez pas SQL Server 2017 / Azure Analysis Services (1400) dans la zone de liste de niveau de compatibilité, vous n’utilisez pas la dernière version de SQL Server Data Tools. Pour obtenir la version la plus récente, consultez [Installer les outils de données SQL Server](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt).  
      
  
## <a name="understanding-the-ssdt-tabular-model-authoring-environment"></a>Présentation du modèle tabulaire SSDT environnement de création  

Maintenant que vous avez créé un nouveau projet de modèle tabulaire, prenons un moment pour Explorer le modèle tabulaire, environnement de création dans Visual Studio.  
  
Une fois votre projet est créé, il s’ouvre dans Visual Studio. Sur le côté droit, dans **Explorateur de modèles tabulaires**, vous afficher une arborescence des objets dans votre modèle. Étant donné que vous n’avez pas encore importé de données, les dossiers sont vides. Vous pouvez cliquer sur un dossier de l’objet pour effectuer des actions, similaires à la barre de menus. À mesure que vous parcourez ce didacticiel, vous utilisez l’Explorateur de modèles tabulaires pour naviguer parmi les différents objets dans votre projet de modèle.

![as-lesson1-tme](../tutorial-tabular-1400/media/as-lesson1-tme.png)

Cliquez sur le **l’Explorateur de solutions** onglet. Ici, vous voyez votre **Model.bim** fichier. Si vous ne voyez pas la fenêtre du concepteur vers la gauche (la fenêtre vide avec l’onglet Model.bim), dans **l’Explorateur de solutions**, sous **projet AW Internet Sales**, double-cliquez sur le **Model.bim** fichier. Le fichier Model.bim contient les métadonnées pour votre projet de modèle. 

![as-lesson1-se](../tutorial-tabular-1400/media/as-lesson1-se.png)
  
Cliquez sur **Model.bim**. Dans le **propriétés** , vous devez voir les propriétés du modèle, la plus importantes qui est la **DirectQuery Mode** propriété. Cette propriété spécifie si le modèle est déployé en mode In-Memory (désactivé) ou en mode DirectQuery (activé). Pour ce didacticiel, vous créez et déployez votre modèle en mode In-Memory.

![en tant que-lesson1-properties](../tutorial-tabular-1400/media/as-lesson1-properties.png)
  
Lorsque vous créez un projet de modèle, certaines de ses propriétés sont définies automatiquement en fonction des paramètres de modélisation des données qui peuvent être spécifiés dans le **outils** menu > **Options** boîte de dialogue. Les propriétés de sauvegarde de données, de rétention de l'espace de travail et du serveur de l'espace de travail spécifient comment et où la base de données d'espace de travail (votre base de données de conception de modèle) est sauvegardée, conservée en mémoire et construite. Vous pouvez modifier ces paramètres ultérieurement si nécessaire, mais pour l’instant, laissez ces propriétés comme ils le sont.  

Dans **l’Explorateur de solutions**, avec le bouton droit **AW Internet Sales** (projet), puis cliquez sur **propriétés**. Le **Pages de propriétés de AW Internet Sales** boîte de dialogue s’affiche. Vous définissez certaines de ces propriétés ultérieurement lorsque vous déployez votre modèle.  
  
Lorsque vous avez installé SSDT, plusieurs nouveaux éléments de menu ont été ajoutées à l’environnement Visual Studio. Cliquez sur le **modèle** menu. À ce stade, vous pouvez importer des données, actualiser les données de l’espace de travail, parcourir votre modèle dans Excel, créer des perspectives et des rôles, sélectionner la vue du modèle et définir les options de calcul. Cliquez sur le **Table** menu. À ce stade, vous pouvez créer et gérer les relations, spécifier les paramètres de table de dates, créer des partitions et modifier les propriétés de la table. Si vous cliquez sur le **colonne** menu, vous pouvez ajouter et supprimer des colonnes dans une table, figer des colonnes et spécifier l’ordre de tri. SSDT ajoute également des boutons à la barre. La fonction Somme automatique pour créer une mesure d’agrégation standard pour une colonne sélectionnée est plus pratique. D'autres boutons de la barre d'outils permettent d'accéder rapidement aux fonctionnalités et aux commandes fréquemment utilisées.  
  
Explorez les boîtes de dialogue et les emplacements des fonctionnalités spécifiques à la création des modèles tabulaires. Alors que certains éléments ne sont pas encore actives, vous pouvez obtenir une bonne idée de l’environnement de création de modèles tabulaires.  
  

## <a name="whats-next"></a>Quelle est l’étape suivante ?

[Leçon 2 : Obtenir des données](../tutorial-tabular-1400/as-lesson-2-get-data.md).

  
  
  
