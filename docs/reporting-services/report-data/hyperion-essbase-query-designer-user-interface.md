---
title: "Interface d’utilisateur du concepteur Hyperion Essbase requête | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- "10013"
- sql13.rtp.rptdesigner.dataview.hyperionessbasequerydesigner.f1
helpviewer_keywords:
- Hyperion Essbase Query Designer
- data sources [Reporting Services], Hyperion Essbase
- multidimensional data [Reporting Services]
- query designers [Reporting Services]
- Hyperion Essbase [Reporting Services], query designer
ms.assetid: bc91b422-c6ab-4062-a300-8290fae6191b
caps.latest.revision: 23
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 68a0a5da224c0f6f78eca8df1ae766e85d7750f2
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="hyperion-essbase-query-designer-user-interface"></a>Interface utilisateur du Concepteur de requêtes Hyperion Essbase
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] fournit un concepteur de requêtes graphique permettant de générer des requêtes MDX (Multidimensional Expression) pour une source de données [!INCLUDE[extEssbase](../../includes/extessbase-md.md)]. Le concepteur de requêtes graphique MDX comporte deux modes : le mode Création et le mode Requête. Chaque mode fournit un volet Métadonnées à partir duquel vous pouvez faire glisser des membres d'un cube défini sur la source de données pour créer une requête MDX qui récupère des données lors du traitement du rapport.  
  
> [!IMPORTANT]  
>  Les utilisateurs accèdent aux sources de données lorsqu'ils créent et exécutent des requêtes. Vous devez accorder des autorisations minimales sur les sources de données, telles que des autorisations en lecture seule.  
  
 Pour plus d’informations sur l’utilisation d’une source de données multidimensionnelle [!INCLUDE[extEssbase](../../includes/extessbase-md.md)], consultez [Type de connexion Hyperion Essbase &#40;SSRS&#41;](../../reporting-services/report-data/hyperion-essbase-connection-type-ssrs.md).  
  
 Cette section décrit les boutons de la barre d'outils et les volets du Concepteur de requêtes pour chaque mode du concepteur de requêtes graphique.  
  
## <a name="graphical-query-designer-in-design-mode"></a>Concepteur de requêtes graphique en mode Création  
 Lorsque vous modifiez une requête MDX pour un dataset qui utilise une source de données [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] , le concepteur de requêtes graphique s'ouvre en mode Création.  
  
 La figure suivante présente les différents volets du mode Création.  
  
 ![Concepteur de requêtes pour la source de données Hyperion Essbase](../../reporting-services/report-data/media/rsqd-dshyperionessbase-mdx-designmode.gif "Concepteur de requêtes pour la source de données Hyperion Essbase")  
  
 Le tableau suivant répertorie les volets disponibles dans ce mode.  
  
|Volet|Fonction|  
|----------|--------------|  
|Bouton Sélection de cube|Affiche le cube actuellement sélectionné.|  
|Volet Métadonnées|Affiche une liste hiérarchique des cubes.|  
|Volet Membres calculés|Affiche les membres calculés actuellement définis et disponibles pour être utilisés dans la requête.|  
|Volet Filtre|Affiche les filtres à appliquer dans la requête.|  
|Volet Données|Affiche les résultats de l'exécution de la requête.|  
  
 Vous pouvez faire glisser des dimensions et des mesures à partir du volet Métadonnées, ainsi que des membres calculés à partir du volet Membres calculés, dans le volet Données. Si le bouton bascule **Exécution automatique** de la barre d'outils est activé, le Concepteur de requêtes exécute la requête chaque fois que vous déposez un objet dans le volet Données. Si le bouton **Exécution automatique** est désactivé, le Concepteur de requêtes n'exécute pas la requête lorsque vous effectuez des modifications dans le volet Données. Vous pouvez exécuter la requête manuellement en utilisant le bouton **Exécuter** de la barre d'outils.  
  
 Dans le volet Filtre, vous pouvez sélectionner des valeurs de dimension pour limiter les données extraites de la source de données. Les valeurs que vous définissez dans le filtre en mode Création apparaissent dans la clause MDX Where en mode Requête.  
  
### <a name="toolbar-for-the-graphical-query-designer-in-design-mode-toolbar"></a>Barre d'outils du concepteur de requêtes graphique en mode Création  
 La barre d'outils du Concepteur de requêtes fournit des boutons qui vous aident à concevoir des requêtes MDX à l'aide de l'interface graphique. Le tableau suivant décrit ces boutons et leurs fonctions.  
  
|Bouton|Description|  
|------------|-----------------|  
|**Modifier en tant que texte**|Bascule entre le Concepteur de requêtes textuel et le concepteur de requêtes graphique. Non disponible pour ce type de source de données.|  
|**Importer**|Importe une requête existante à partir d'un fichier de définition de rapport (.rdl) sur le système de fichiers. Pour plus d’informations, consultez [Datasets incorporés dans le rapport et datasets partagés &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).|  
|![Actualiser les champs de dataset](../../reporting-services/report-data/media/rsqdicon-refreshfields.gif "actualiser les champs de dataset")|Actualise les métadonnées à partir de la source de données.|  
|![Add calculated member](../../reporting-services/report-data/media/rsqdicon-addcalculatedmember.gif "Add calculated member")|Affiche la boîte de dialogue **Générateur de membres calculés** . Permet de créer ou de modifier des expressions pour un membre calculé, y compris le paramètre de la propriété **Ordre de résolution** .|  
|![Bouton bascule pour afficher les cellules vides](../../reporting-services/report-data/media/rsqdicon-showemptycells.gif "bascule pour afficher les cellules vides")|Affiche ou masque les cellules vides dans le volet Données. (Cela revient à utiliser la clause NON EMPTY dans MDX.)|  
|![Exécuter automatiquement la requête](../../reporting-services/report-data/media/rsqdicon-autoexecute.gif "exécuter automatiquement la requête")|Exécute automatiquement la requête et affiche le résultat chaque fois qu'une modification est effectuée, par exemple lorsqu'une colonne est supprimée du volet Données. Les résultats s'affichent dans le volet Données.|  
|![Supprimer](../../reporting-services/report-data/media/rsqdicon-delete.gif "Supprimer")|Supprime l'élément sélectionné de la requête. Utilisez ce bouton pour supprimer les lignes sélectionnées dans le volet Filtre.|  
|![Exécuter la requête](../../reporting-services/report-data/media/rsqdicon-run.gif "Exécuter la requête")|Exécute la requête et affiche les résultats dans le volet Données.|  
|![Annuler la requête](../../reporting-services/report-data/media/rsqdicon-cancel.gif "annuler la requête")|Annule la requête.|  
|![Basculez en mode Création](../../reporting-services/media/rsqdicon-designmode.gif "basculer en mode Design")|Bascule entre le mode Création et le mode Requête.|  
  
## <a name="graphical-query-designer-in-query-mode"></a>Concepteur de requêtes graphique en mode Requête  
 Pour basculer vers le mode Requête du concepteur de requêtes graphique, cliquez sur le bouton bascule **Mode Création** dans la barre d'outils. L'illustration suivante présente les composants du Concepteur de requêtes en mode Requête.  
  
 ![Concepteur de requêtes en Mode requête pour Hyperion](../../reporting-services/report-data/media/rsqd-hyperionessbase-mdx-querymode.gif "Concepteur de requêtes en Mode requête pour Hyperion")  
  
 Le tableau ci-dessous décrit la fonction de chaque volet.  
  
|Volet|Fonction|  
|----------|--------------|  
|Bouton Sélection de cube|Affiche le cube actuellement sélectionné.|  
|Volet Métadonnées/Fonctions|Affiche une fenêtre à onglets qui présente une liste des métadonnées ou des fonctions disponibles qui peuvent être utilisées pour créer le texte de la requête.|  
|Volet Requête|Affiche le texte de la requête actuelle.|  
|Volet Résultat|Affiche les résultats de la requête.|  
  
 À partir du volet Métadonnées, vous pouvez faire glisser des mesures et des dimensions depuis l'onglet **Métadonnées** vers le volet Requête MDX. Vous pouvez faire glisser des fonctions à partir de l'onglet **Fonctions** dans le volet Requête MDX. Lorsque vous exécutez la requête, le volet Résultat affiche les résultats pour la requête MDX actuelle.  
  
### <a name="toolbar-for-the-graphical-query-designer-in-query-mode"></a>Barre d'outils du concepteur de requêtes graphique en mode Requête  
 La barre d'outils du Concepteur de requêtes fournit des boutons qui vous aident à concevoir des requêtes MDX à l'aide de l'interface graphique. Les boutons de la barre d'outils sont identiques en mode Création et en mode Requête, mais les boutons suivants ne sont pas activés en mode Requête :  
  
-   **Modifier en tant que texte**  
  
-   **Ajouter un membre calculé** (![Add calculated member](../../reporting-services/report-data/media/rsqdicon-addcalculatedmember.gif "Add calculated member"))  
  
-   **Afficher les cellules vides** (![bascule pour afficher les cellules vides](../../reporting-services/report-data/media/rsqdicon-showemptycells.gif "bascule pour afficher les cellules vides"))  
  
-   **Exécution automatique** (![exécuter automatiquement la requête](../../reporting-services/report-data/media/rsqdicon-autoexecute.gif "exécuter automatiquement la requête"))  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un Dataset partagé ou Dataset incorporé &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)   
 [Fichier de Configuration RSReportDesigner](../../reporting-services/report-server/rsreportdesigner-configuration-file.md)  
  
  
