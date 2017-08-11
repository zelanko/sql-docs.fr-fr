---
title: "Interface utilisateur du Concepteur de requêtes MDX de Analysis Services | Documents Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- "10012"
- sql13.rtp.rptdesigner.dataview.asquerydesigner.f1
helpviewer_keywords:
- MDX [Reporting Services], creating datasets
- query designers [Reporting Services]
ms.assetid: d9c7c0b3-fce4-4a65-b679-408273e6a925
caps.latest.revision: 38
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 7f8838c9793cfc4a8e38bea3f0f27e702dd27e4d
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="analysis-services-mdx-query-designer-user-interface"></a>Interface utilisateur du Concepteur de requêtes MDX Analysis Services
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] fournit des concepteurs de requêtes graphiques pour la création de requêtes MDX (Multidimensional Expression) et DMX (Data Mining Expression) pour une source de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Cette rubrique offre une description du Concepteur de requêtes MDX. Pour plus d’informations sur le Concepteur de requêtes DMX, consultez [Type de connexion Analysis Services pour DMX &#40;SSRS&#41;](../../reporting-services/report-data/analysis-services-connection-type-for-dmx-ssrs.md).  
  
 Le concepteur de requêtes graphique MDX comporte deux modes : le mode Création et le mode Requête. Chaque mode fournit un volet Métadonnées à partir duquel vous pouvez faire glisser des membres de cubes sélectionnés pour créer une requête MDX qui récupère des données lors du traitement du rapport.  
  
> [!IMPORTANT]  
>  Les utilisateurs accèdent aux sources de données lorsqu'ils créent et exécutent des requêtes. Vous devez accorder des autorisations minimales sur les sources de données, telles que des autorisations en lecture seule.  
  
> [!NOTE]  
>  L'importation d'une requête .mdx à partir d'un fichier n'est pas prise en charge.  
  
## <a name="graphical-mdx-query-designer-in-design-mode"></a>Concepteur de requêtes MDX graphique en mode Création  
 Lorsque vous modifiez une requête MDX pour un dataset de rapport, le concepteur de requêtes MDX graphique s'ouvre en mode Création.  
  
 La figure suivante présente les différents volets du mode Création.  
  
 ![Concepteur de requêtes Analysis Services MDX, le mode design](../../reporting-services/report-data/media/rsqd-dsawas-mdx-designmode.gif "Concepteur de requêtes MDX Analysis Services, le mode design")  
  
 Le tableau suivant répertorie les volets disponibles dans ce mode :  
  
|Volet|Fonction|  
|----------|--------------|  
|Bouton Sélection de cube (**...**)|Affiche le cube actuellement sélectionné.|  
|Volet Métadonnées|Affiche une liste hiérarchique des mesures, des indicateurs de performance clés (KPI) et des dimensions définis dans le cube sélectionné.|  
|Volet Membres calculés|Affiche les membres calculés actuellement définis et disponibles pour être utilisés dans la requête.|  
|Volet Filtre|Utilisez ce volet pour choisir des dimensions et hiérarchies associées afin de filtrer des données à la source et de limiter la quantité de données retournée dans le rapport.|  
|Volet Données|Affiche les en-têtes de colonne pour le jeu de résultats au fur et à mesure que vous faites glisser des éléments des volets Métadonnées et Membres calculés. Met automatiquement à jour le jeu de résultats si le bouton **Exécution automatique** est sélectionné. .|  
  
 Vous pouvez faire glisser des dimensions, des mesures et des indicateurs de performance clés à partir du volet Métadonnées, ainsi que des membres calculés à partir du volet Membres calculés, dans le volet Données. Dans le volet Filtre, vous pouvez sélectionner des dimensions et des hiérarchies associées et définir des expressions de filtres pour limiter les données disponibles à rechercher. Si le **exécution automatique** (![exécuter automatiquement la requête](../../reporting-services/report-data/media/rsqdicon-autoexecute.gif "exécuter automatiquement la requête")) sur la barre d’outils bouton bascule est sélectionnée, le Concepteur de requêtes exécute la requête chaque fois que vous supprimez un objet de métadonnées dans le volet données. Vous pouvez exécuter manuellement la requête à l’aide de la **exécuter** (![exécuter la requête](../../reporting-services/report-data/media/rsqdicon-run.gif "exécuter la requête")) dans la barre d’outils.  
  
 Lorsque vous créez une requête MDX dans ce mode, les propriétés supplémentaires suivantes sont automatiquement incluses dans la requête :  
  
 **Propriétés de membre** MEMBER_CAPTION, MEMBER_UNIQUE_NAME  
  
 **Propriétés de cellule** VALUE, BACK_COLOR, FORE_COLOR, FORMATTED_VALUE, FORMAT_STRING, FONT_NAME, FONT_SIZE, FONT_FLAGS  
  
 Pour spécifier vos propres propriétés supplémentaires, vous devez modifier manuellement la requête MDX en mode Requête.  
  
### <a name="graphical-mdx-query-designer-toolbar-in-design-mode"></a>Barre d'outils du Concepteur de requêtes graphique MDX en mode Création  
 La barre d'outils du Concepteur de requêtes fournit des boutons qui vous aident à concevoir des requêtes MDX à l'aide de l'interface graphique. Le tableau suivant répertorie ces boutons et leurs fonctions.  
  
|Bouton|Description|  
|------------|-----------------|  
|**Modifier en tant que texte**|Non activé pour ce type de source de données.|  
|**Importer**|Importe une requête existante à partir d'un fichier de définition de rapport (.rdl) sur le système de fichiers. Pour plus d’informations, consultez [Datasets incorporés dans le rapport et datasets partagés &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).|  
|![Passez en mode de requête MDX](../../reporting-services/report-data/media/rsqdicon-commandtypemdx.gif "passer en mode de requête MDX")|Bascule vers le type de commande MDX.|  
|![Remplacez par la vue langage de requête DMX](../../reporting-services/report-data/media/rsqdicon-commandtypedmx.gif "modifier en vue de langage de requête DMX")|Bascule vers le type de commande DMX.|  
|![Actualiser les données de résultat](../../reporting-services/report-data/media/rsqdicon-refresh.gif "actualiser les données de résultat")|Actualise les métadonnées à partir de la source de données.|  
|![Add calculated member](../../reporting-services/report-data/media/rsqdicon-addcalculatedmember.gif "Add calculated member")|Affiche la boîte de dialogue **Générateur de membres calculés** .|  
|![Bouton bascule pour afficher les cellules vides](../../reporting-services/report-data/media/rsqdicon-showemptycells.gif "bascule pour afficher les cellules vides")|Affiche ou masque les cellules vides dans le volet Données. (Cela revient à utiliser la clause NON EMPTY dans MDX.)|  
|![Exécuter automatiquement la requête](../../reporting-services/report-data/media/rsqdicon-autoexecute.gif "exécuter automatiquement la requête")|Exécute automatiquement la requête et affiche le résultat chaque fois qu'une modification est effectuée. Les résultats s'affichent dans le volet Données.|  
|![Bouton Afficher les agrégations](../../reporting-services/report-data/media/rsqdicon-showaggregations.gif "bouton d’afficher les agrégations")|Affiche les agrégations dans le volet Données.|  
|![Supprimer](../../reporting-services/report-data/media/rsqdicon-delete.gif "Supprimer")|Supprime de la requête la colonne sélectionnée dans le volet Données.|  
|![Icône de la boîte de dialogue Paramètres de requête](../../reporting-services/report-data/media/iconqueryparameter.gif "icône de la boîte de dialogue Paramètres de requête")|Affiche la boîte de dialogue **Paramètres de la requête** . Lorsque vous spécifiez des valeurs pour un paramètre de requête, un paramètre de rapport du même nom est automatiquement créé. Le paramètre de requête prend pour valeur une expression qui fait référence au paramètre de rapport.|  
|![Bouton de la requête de préparation](../../reporting-services/report-data/media/rsqdicon-preparequery.gif "bouton préparer la requête")|Prépare la requête.|  
|![Exécuter la requête](../../reporting-services/report-data/media/rsqdicon-run.gif "Exécuter la requête")|Exécute la requête et affiche les résultats dans le volet Données.|  
|![Annuler la requête](../../reporting-services/report-data/media/rsqdicon-cancel.gif "annuler la requête")|Annule la requête.|  
|![Basculez en mode Création](../../reporting-services/media/rsqdicon-designmode.gif "basculer en mode Design")|Bascule entre le mode Création et le mode Requête.|  
  
## <a name="graphical-mdx-query-designer-in-query-mode"></a>Concepteur de requêtes graphique MDX en mode Requête  
 Pour basculer en mode **Requête** dans le concepteur de requêtes graphique, cliquez sur le bouton bascule **Mode Création** dans la barre d'outils.  
  
 La figure suivante présente les différents volets du mode Requête.  
  
 ![Analysis Services MDX Concepteur de requêtes, requête affichage](../../reporting-services/report-data/media/rsqd-dsawas-mdx-querymode.gif "MDX Analysis Services Concepteur de requêtes, requête affichage")  
  
 Le tableau suivant répertorie les volets disponibles dans ce mode :  
  
|Volet|Fonction|  
|----------|--------------|  
|Bouton Sélection de cube (**...**)|Affiche le cube actuellement sélectionné.|  
|Volet Métadonnées/Fonctions/Modèles|Affiche une liste hiérarchique des mesures, des indicateurs de performance clés (KPI) et des dimensions définis dans le cube sélectionné.|  
|Volet Requête|Affiche le texte de la requête.|  
|Volet Résultat|Affiche les résultats de l'exécution de la requête.|  
  
 Le volet Métadonnées affiche les onglets **Métadonnées**, **Fonctions**et **Modèles**. À partir de l'onglet **Métadonnées** , vous pouvez faire glisser des dimensions, des hiérarchies et des valeurs de performance clés dans le volet Requête MDX. À partir de l'onglet **Fonctions** , vous pouvez faire glisser des fonctions dans le volet Requête MDX. À partir de l'onglet **Modèles** , vous pouvez ajouter des modèles MDX dans le volet Requête MDX. Lorsque vous exécutez la requête, le volet Résultat affiche les résultats pour la requête MDX.  
  
 Vous pouvez étendre la requête MDX par défaut générée en mode Création de façon à inclure des propriétés de membre et de cellule supplémentaires. Lorsque vous exécutez la requête, ces valeurs n'apparaissent pas dans le jeu de résultats. Toutefois, elles sont renvoyées à [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et vous pouvez utiliser ces valeurs dans un rapport. Pour plus d’informations, consultez [Propriétés de champ étendues pour une base de données Analysis Services &#40;SSRS&#41;](../../reporting-services/report-data/extended-field-properties-for-an-analysis-services-database-ssrs.md).  
  
### <a name="graphical-query-designer-toolbar-in-query-mode"></a>Barre d'outils du concepteur de requêtes graphique en mode Requête  
 La barre d'outils du Concepteur de requêtes fournit des boutons qui vous aident à concevoir des requêtes MDX à l'aide de l'interface graphique.  
  
 Les boutons de la barre d'outils sont identiques en mode Création et en mode Requête, mais les boutons suivants ne sont pas activés en mode Requête :  
  
-   **Modifier en tant que texte**  
  
-   **Ajouter un membre calculé** (![Add calculated member](../../reporting-services/report-data/media/rsqdicon-addcalculatedmember.gif "Add calculated member"))  
  
-   **Afficher les cellules vides** (![bascule pour afficher les cellules vides](../../reporting-services/report-data/media/rsqdicon-showemptycells.gif "bascule pour afficher les cellules vides"))  
  
-   **Exécution automatique** (![exécuter automatiquement la requête](../../reporting-services/report-data/media/rsqdicon-autoexecute.gif "exécuter automatiquement la requête"))  
  
-   **Afficher les agrégations** (![bouton d’afficher les agrégations](../../reporting-services/report-data/media/rsqdicon-showaggregations.gif "bouton d’afficher les agrégations"))  
  
## <a name="see-also"></a>Voir aussi  
 [Définir des paramètres dans le Concepteur de requêtes MDX pour Analysis Services &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-data/define-parameters-in-the-mdx-query-designer-for-analysis-services.md)   
 [Créer un Dataset partagé ou Dataset incorporé &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)   
 [Type de connexion Analysis Services pour DMX &#40; SSRS &#41;](../../reporting-services/report-data/analysis-services-connection-type-for-dmx-ssrs.md)   
 [Fichier de Configuration RSReportDesigner](../../reporting-services/report-server/rsreportdesigner-configuration-file.md)   
 [Type de connexion Analysis Services pour MDX &#40; SSRS &#41;](../../reporting-services/report-data/analysis-services-connection-type-for-mdx-ssrs.md)  
  
  
