---
title: Interface utilisateur du concepteur (Générateur de rapports) de SAP NetWeaver BI Query | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10014"
helpviewer_keywords:
- query designers, SAP
ms.assetid: 8edda06d-1608-498b-bd50-10905e54f6ce
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: af04c7697d685fe36c34b09060302756f6f51214
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48127424"
---
# <a name="sap-netweaver-bi-query-designer-user-interface-report-builder"></a>Interface utilisateur du Concepteur de requêtes SAP NetWeaver BI (Générateur de rapports)
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] fournit un concepteur de requêtes graphique permettant de générer des requêtes MDX (Multidimensional Expression) pour une source de données SAP NetWeaver® Business Intelligence. Le concepteur de requêtes graphique MDX comporte deux modes : le mode Création et le mode Requête. Chaque mode fournit un volet Métadonnées à partir duquel vous pouvez faire glisser des membres à partir d'InfoCube, de MultiProvider ou d'une requête Web définie sur la source de données, afin de générer une requête MDX visant à récupérer des données lors du traitement du rapport.  
  
> [!IMPORTANT]  
>  Les utilisateurs accèdent aux sources de données lorsqu'ils créent et exécutent des requêtes. Vous devez accorder des autorisations minimales sur les sources de données, telles que des autorisations en lecture seule.  
  
 Cette section décrit les boutons de la barre d'outils et les volets du Concepteur de requêtes pour chaque mode du concepteur de requêtes graphique.  
  
## <a name="graphical-query-designer-in-design-mode"></a>Concepteur de requêtes graphique en mode Création  
 Lorsque vous modifiez une requête de dataset qui utilise une source de données [!INCLUDE[SAP_DPE_BW_1](../includes/sap-dpe-bw-1-md.md)] , le concepteur de requêtes graphique s'ouvre en mode Création.  
  
 ![Concepteur de requêtes avec MDX en mode Création](media/rsqd-dssapbw-mdx-designmode.gif "Concepteur de requêtes avec MDX en mode Création")  
  
 Le tableau suivant répertorie les volets disponibles dans ce mode.  
  
|Volet|Fonction|  
|----------|--------------|  
|Bouton Sélection de cube|Affiche l'InfoCube, le MultiProvider ou la requête Web actuellement sélectionné.|  
|Volet Métadonnées|Affiche une liste hiérarchique des InfoCubes, MultiProviders et des requêtes. Les requêtes créées sur la source de données peuvent apparaître sous le cube correspondant.|  
|Volet Membres calculés|Affiche les membres calculés actuellement définis et disponibles pour être utilisés dans la requête.|  
|Volet Données|Affiche les résultats de l'exécution de la requête.|  
  
 Vous pouvez faire glisser des dimensions et des chiffres clés à partir du volet Métadonnées ainsi que des membres calculés à partir du volet Membres calculés dans le volet Données. Si le bouton bascule **Exécution automatique** de la barre d'outils est activé, le Concepteur de requêtes exécute la requête chaque fois que vous déposez un objet dans le volet Données. Si le bouton **Exécution automatique** est désactivé, le Concepteur de requêtes n'exécute pas la requête lorsque vous effectuez des modifications dans le volet Données. Vous pouvez exécuter la requête manuellement en utilisant le bouton **Exécuter** de la barre d'outils.  
  
### <a name="toolbar-for-the-graphical-query-designer-in-design-mode-toolbar"></a>Barre d'outils du concepteur de requêtes graphique en mode Création  
 La barre d'outils du Concepteur de requêtes fournit des boutons qui vous aident à concevoir des requêtes MDX à l'aide de l'interface graphique. Le tableau suivant décrit ces boutons et leurs fonctions.  
  
|Bouton|Description|  
|------------|-----------------|  
|**Modifier en tant que texte**|Bascule entre le Concepteur de requêtes textuel et le concepteur de requêtes graphique. Non disponible pour ce type de source de données.|  
|**Importer**|Importe une requête existante à partir d'un fichier de définition de rapport (.rdl) sur le système de fichiers.|  
|![Actualiser les champs du dataset](media/rsqdicon-refreshfields.gif "Actualiser les champs du dataset")|Actualise les métadonnées à partir de la source de données.|  
|![Ajouter un membre calculé](../analysis-services/media/rsqdicon-addcalculatedmember.gif "ajouter un membre calculé")|Affiche la boîte de dialogue **Générateur de membres calculés** .|  
|![Bouton bascule pour afficher les cellules vides](../analysis-services/media/rsqdicon-showemptycells.gif "Bouton bascule pour afficher les cellules vides")|Affiche ou masque les cellules vides dans le volet Données. (Cela revient à utiliser la clause NON EMPTY dans MDX.)|  
|![Exécuter automatiquement la requête](../analysis-services/media/rsqdicon-autoexecute.gif "Exécuter automatiquement la requête")|Exécute automatiquement la requête et affiche le résultat chaque fois qu'une modification est effectuée, par exemple lorsqu'une colonne est supprimée du volet Données. Les résultats s'affichent dans le volet Données.|  
|![Supprimer](../analysis-services/media/rsqdicon-delete.gif "supprimer")|Supprime de la requête la colonne sélectionnée dans le volet Données.|  
|![Icône de la boîte de dialogue Paramètres de la requête](../analysis-services/media/iconqueryparameter.gif "Icône de la boîte de dialogue Paramètres de la requête")|Affiche la boîte de dialogue **Variables** . Ce bouton est activé uniquement lorsque le cube sélectionné est un cube de requête (car seuls les cubes de requête prennent en charge les variables). Lorsque vous affectez une valeur par défaut à une variable, un paramètre de rapport correspondant est créé.|  
|![Exécuter la requête](../analysis-services/media/rsqdicon-run.gif "Exécuter la requête")|Exécute la requête et affiche les résultats dans le volet Données.|  
|![Annuler la requête](../analysis-services/media/rsqdicon-cancel.gif "Annuler la requête")|Annule la requête.|  
|![Basculer en mode Création](../analysis-services/media/rsqdicon-designmode.gif "Basculer en mode Design")|Bascule entre le mode Création et le mode Requête.|  
  
## <a name="graphical-query-designer-in-query-mode"></a>Concepteur de requêtes graphique en mode Requête  
 Pour basculer vers le mode Requête du concepteur de requêtes graphique, cliquez sur le bouton bascule **Mode Création** dans la barre d'outils.  
  
 L'illustration suivante présente les composants du Concepteur de requêtes en mode Requête.  
  
 ![Concepteur de requêtes SAP BW MDX en mode Requête](media/rsqd-dssapbw-mdx-querymode.gif "Concepteur de requêtes SAP BW MDX en mode Requête")  
  
 Le tableau ci-dessous décrit la fonction de chaque volet.  
  
|Volet|Fonction|  
|----------|--------------|  
|Bouton Sélection de cube|Affiche l'InfoCube, le MultiProvider ou tout autre cube actuellement sélectionnés.|  
|Volet Métadonnées/Fonctions|Affiche une fenêtre à onglets qui présente une liste des métadonnées ou des fonctions disponibles qui peuvent être utilisées pour créer le texte de la requête.|  
|Volet Variables|Affiche les variables actuellement définies et disponibles pour être utilisées dans la requête.|  
|Volet Requête|Affiche le texte de la requête actuelle.|  
|Volet Résultat|Affiche les résultats de la requête.|  
  
 Dans le volet Métadonnées, vous pouvez faire glisser des chiffres clés et des dimensions à partir de l’onglet **Métadonnées** vers le volet Requête MDX. Le nom technique des métadonnées est inséré à l’emplacement du curseur. Vous pouvez faire glisser des fonctions à partir de l'onglet **Fonctions** dans le volet Requête MDX. Lorsque vous exécutez la requête, le volet Résultat affiche les résultats pour la requête MDX actuelle.  
  
 Si votre cube sélectionné est une requête Web, vous serez invité à définir des valeurs statiques par défaut pour les variables existantes. Vous pouvez ensuite faire glisser des variables dans le volet Requête MDX.  
  
 Les volets Métadonnées et Variables affichent des noms conviviaux. Lorsque vous déposez les objets dans le volet Requête MDX, les noms techniques requis par la source de données spécifiée dans la requête MDX s'affichent.  
  
### <a name="toolbar-for-the-graphical-query-designer-in-query-mode"></a>Barre d'outils du concepteur de requêtes graphique en mode Requête  
 La barre d'outils du Concepteur de requêtes fournit des boutons qui vous aident à concevoir des requêtes MDX à l'aide de l'interface graphique. Les boutons de la barre d'outils sont identiques en mode Création et en mode Requête, mais les boutons suivants ne sont pas activés en mode Requête :  
  
-   **Modifier en tant que texte**  
  
-   **Ajouter un membre calculé** (![ajouter un membre calculé](../analysis-services/media/rsqdicon-addcalculatedmember.gif "ajouter un membre calculé"))  
  
-   **Afficher les cellules vides** (![Bouton bascule pour afficher les cellules vides](../analysis-services/media/rsqdicon-showemptycells.gif "Bouton bascule pour afficher les cellules vides"))  
  
-   **Exécution automatique** (![Exécuter automatiquement la requête](../analysis-services/media/rsqdicon-autoexecute.gif "Exécuter automatiquement la requête"))  
  
-   **Supprimer** (![supprimer](../analysis-services/media/rsqdicon-delete.gif "supprimer"))  
  
## <a name="see-also"></a>Voir aussi  
 [Concepteurs de requêtes &#40;Générateur de rapports&#41;](../../2014/reporting-services/query-designers-report-builder.md)  
  
  
