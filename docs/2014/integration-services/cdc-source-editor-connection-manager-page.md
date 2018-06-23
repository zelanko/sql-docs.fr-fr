---
title: Éditeur de Source CDC (Page Gestionnaire de connexions) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.ssis.designer.cdcsource.connection.f1
ms.assetid: 304e6717-e160-4a7b-a06f-32182449fef8
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: f60c9562a611ca3f396456abd80fb65c4fb5a99a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36038626"
---
# <a name="cdc-source-editor-connection-manager-page"></a>Éditeur de source CDC (page Gestionnaire de connexions)
  Utilisez la page **Gestionnaire de connexions** de la boîte de dialogue **Éditeur de source CDC** pour sélectionner le gestionnaire de connexions ADO.NET de la base de données [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] à partir de laquelle la source CDC lit les lignes modifiées (la base de données CDC). Une fois la base de données CDC sélectionnée, vous devez sélectionner une table capturée dans la base de données.  
  
 Pour plus d'informations sur la source CDC, consultez [CDC Source](data-flow/cdc-source.md).  
  
## <a name="task-list"></a>Liste des tâches  
 **Pour ouvrir l'Éditeur de source CDC (page Gestionnaire de connexions)**  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], ouvrez le package [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] qui possède la source CDC.  
  
2.  Sous l’onglet **Flux de données** , double-cliquez sur la source CDC.  
  
3.  Dans **l’Éditeur de source CDC**, cliquez sur **Gestionnaire de connexions**.  
  
## <a name="options"></a>Options  
 **Gestionnaire de connexions ADO.NET**  
 Sélectionnez un gestionnaire de connexions existant dans la liste ou cliquez sur **Nouveau** pour créer une connexion. La connexion doit être établie avec une base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] activée pour la capture de données modifiées et dans laquelle la table de modifications sélectionnée est localisée.  
  
 **Nouveau**  
 Cliquez sur **Nouveau**. La boîte de dialogue **Configurer l’Éditeur du gestionnaire de connexions ADO.NET** s’ouvre et vous permet de créer un gestionnaire de connexions.  
  
 **Table CDC**  
 Sélectionnez la table source CDC qui contient les modifications capturées que vous souhaitez lire et envoyer aux composants SSIS en aval pour le traitement.  
  
 **Instance de capture**  
 Sélectionnez ou tapez le nom de l'instance de capture CDC avec la table CDC à lire.  
  
 Une table source capturée peut contenir une ou deux instances capturées pour gérer la transition transparente de la définition de table lors des modifications de schéma. Si plusieurs instances de capture sont définies pour la table source qui est capturée, sélectionnez l'instance de capture à utiliser ici. Le nom par défaut de l’instance de capture pour une table [schema].[table] est \<schéma>_\<table>, mais le nom réel utilisé pour cette instance de capture peut être différent. La table réelle dans laquelle les données sont lues est la table CDC **cdc .\<instance-capture>_CT**.  
  
 **Mode de traitement CDC**  
 Sélectionnez le mode de traitement le plus adapté pour la gestion de vos besoins de traitement. Les options possibles sont les suivantes :  
  
-   **Tout**: retourne les modifications apportées à la plage de capture de données modifiées actuelle sans les valeurs **Avant la mise à jour** .  
  
-   **Tout avec les anciennes valeurs**: retourne les modifications apportées à la plage de traitement de capture de données modifiées actuelle, dont les anciennes valeurs (**Avant la mise à jour**). Chaque opération de mise à jour utilise deux lignes, une avec les valeurs avant la mise à jour et une avec la valeur après la mise à jour.  
  
-   **Net**: retourne une seule ligne de modification par ligne source modifiée dans la plage de capture de données modifiées actuelle. Si une ligne source a été mise à jour plusieurs fois, la modification associée est appliquée (par exemple, l'insertion et la mise à jour sont considérées comme une mise à jour unique, et la mise à jour et la suppression sont considérées comme une suppression unique). Lorsque vous travaillez dans le mode de traitement de modifications Net, il est possible de fractionner les modifications apportées aux sorties de suppression, d'insertion et de mise à jour et de les traiter en parallèle car la ligne source apparaît dans plusieurs sorties.  
  
-   **Net avec masque de mise à jour** : ce mode est semblable au mode Net standard, à ceci près qu’il ajoute des colonnes booléennes au modèle de nom **__$\<nom-colonne>\__Modifié** qui indique les colonnes modifiées dans la ligne de modification active.  
  
-   **Net avec fusion**: ce mode est semblable au mode Net standard, à ceci près que les opérations d’insertion et de mise à jour sont fusionnées en une seule opération de fusion (UPSERT).  
  
> [!NOTE]  
>  Pour toutes les options de modifications Net, la table source doit avoir une clé primaire ou un index unique. Pour les tables sans clé primaire ou sans index unique, vous devez utiliser l’option **Tout** .  
  
 **Variable contenant l'état CDC**  
 Sélectionnez la variable de package de chaîne SSIS qui gère l'état de capture de données modifiées pour le contexte de capture de données modifiées actuel. Pour plus d’informations sur la variable d’état CDC, consultez [Définir une variable d’état](data-flow/define-a-state-variable.md).  
  
 **Inclure la colonne de l'indicateur de retraitement**  
 Cochez cette case pour créer une colonne spéciale de sortie nommée ***** __$reprocessing *****.  
  
 Cette colonne a la valeur **true** quand la plage de traitement CDC chevauche la plage de traitement initiale (la plage de NSE correspondant à la période de charge initiale) ou lorsqu’une plage de traitement CDC est retraitée suite à une erreur lors d’une exécution précédente. Cette colonne d'indicateur permet au développeur SSIS de gérer les erreurs différemment lors du retraitement des modifications (par exemple, les actions telles que la suppression d'une ligne inexistante et une insertion ayant échoué sur une clé dupliquée peuvent être ignorées).  
  
 Pour plus d’informations, consultez [Propriétés personnalisées des sources CDC](data-flow/cdc-source-custom-properties.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de Source CDC &#40;Page colonnes&#41;](../../2014/integration-services/cdc-source-editor-columns-page.md)   
 [Éditeur de Source CDC &#40;Page sortie d’erreur&#41;](../../2014/integration-services/cdc-source-editor-error-output-page.md)  
  
  