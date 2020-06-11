---
title: Concepteur de requêtes MDX Analysis Services (PowerPivot) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b1524b18-b9f1-46d2-a34e-dd7c91ca4684
author: minewiskan
ms.author: owend
ms.openlocfilehash: 34f2ac3dbc81731cf9bb23cf02a8c3bebc931f69
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84528085"
---
# <a name="analysis-services-mdx-query-designer-powerpivot"></a>Concepteur de requêtes MDX Analysis Services (PowerPivot)
  Le concepteur de requêtes MDX (Multidimensional Expression) Analysis Services fournit des interfaces utilisateur graphiques pour vous aider à créer des requêtes MDX pour une [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] source de données. Le concepteur de requêtes graphique MDX comporte deux modes : le mode Création et le mode Requête. Chaque mode fournit un volet Métadonnées à partir duquel vous pouvez faire glisser des membres de cubes sélectionnés pour créer une requête MDX qui extrait les données que vous souhaitez utiliser.  
  
> [!IMPORTANT]  
>  Les utilisateurs accèdent aux sources de données lorsqu'ils créent et exécutent des requêtes. Vous devez accorder des autorisations minimales sur les sources de données, telles que des autorisations en lecture seule.  
  
 Les sections suivantes décrivent les boutons de la barre d'outils et les volets du concepteur de requêtes pour chaque mode du concepteur de requêtes graphique.  
  
## <a name="graphical-mdx-query-designer-in-design-mode"></a>Concepteur de requêtes MDX graphique en mode Création  
 Lorsque vous modifiez une requête MDX, le concepteur de requêtes MDX graphique s'ouvre en mode Création.  
  
 La figure suivante présente les différents volets du mode Création.  
  
 ![Concepteur de requêtes MDX Analysis Services, mode Conception](media/rsqd-dsawas-mdx-designmode.gif "Concepteur de requêtes MDX Analysis Services, mode Conception")  
  
 Le tableau suivant répertorie les volets disponibles dans ce mode :  
  
|Volet|Fonction|  
|----------|--------------|  
|Bouton Sélection de cube (**...**)|Affiche le cube actuellement sélectionné.|  
|Volet Métadonnées|Affiche une liste hiérarchique des mesures, des indicateurs de performance clés (KPI) et des dimensions définis dans le cube sélectionné.|  
|Volet Membres calculés|Affiche les membres calculés actuellement définis et disponibles pour être utilisés dans la requête.|  
|Volet Filtre|Utilisez ce volet pour choisir des dimensions et hiérarchies associées afin de filtrer des données à la source et de limiter la quantité de données retournées.|  
|Volet Données|Affiche les en-têtes de colonne pour le jeu de résultats au fur et à mesure que vous faites glisser des éléments des volets Métadonnées et Membres calculés. Met automatiquement à jour le jeu de résultats si le bouton **Exécution automatique** est sélectionné.|  
  
 Vous pouvez faire glisser des dimensions, des mesures et des indicateurs de performance clés à partir du volet Métadonnées, ainsi que des membres calculés à partir du volet Membres calculés, dans le volet Données. Dans le volet Filtre, vous pouvez sélectionner des dimensions et des hiérarchies associées et définir des expressions de filtres pour limiter les données disponibles à rechercher. Si le bouton bascule **Exécution automatique** (![Exécuter automatiquement la requête](media/rsqdicon-autoexecute.gif "Exécuter automatiquement la requête")) de la barre d’outils est sélectionné, le concepteur de requêtes exécute la requête chaque fois que vous déposez un objet de métadonnées dans le volet Données. Vous pouvez exécuter la requête manuellement en utilisant le bouton **Exécuter** (![Exécuter la requête](media/rsqdicon-run.gif "Exécuter la requête")) de la barre d’outils.  
  
 Lorsque vous créez une requête MDX dans ce mode, les propriétés supplémentaires suivantes sont automatiquement incluses dans la requête :  
  
 **Propriétés de membre** MEMBER_CAPTION, MEMBER_UNIQUE_NAME  
  
 **Propriétés de cellule** VALUE, BACK_COLOR, FORE_COLOR, FORMATTED_VALUE, FORMAT_STRING, FONT_NAME, FONT_SIZE, FONT_FLAGS  
  
 Pour spécifier vos propres propriétés supplémentaires, vous devez modifier manuellement la requête MDX en mode Requête.  
  
 L'importation d'une requête .mdx à partir d'un fichier n'est pas prise en charge.  
  
> [!NOTE]  
>  Pour plus d’informations sur MDX et pour obtenir des informations générales sur le concepteur de requêtes MDX, consultez « Éditeur de requête MDX (Analysis Services - Données multidimensionnelles) » dans la [documentation en ligne de SQL Server](https://go.microsoft.com/fwlink/?linkid=98335).  
  
### <a name="graphical-mdx-query-designer-toolbar-in-design-mode"></a>Barre d'outils du Concepteur de requêtes graphique MDX en mode Création  
 La barre d'outils du Concepteur de requêtes fournit des boutons qui vous aident à concevoir des requêtes MDX à l'aide de l'interface graphique. Le tableau suivant répertorie ces boutons et leurs fonctions.  
  
|Bouton|Description|  
|------------|-----------------|  
|**Modifier en tant que texte**|Non activé pour ce type de source de données.|  
|**Importer**|Importe une requête existante à partir d'un fichier de définition de rapport (.rdl) sur le système de fichiers.|  
|![Basculer vers l'affichage des requêtes MDX](media/rsqdicon-commandtypemdx.gif "Basculer vers l'affichage des requêtes MDX")|Bascule vers le type de commande MDX.|  
|![Actualiser les données du résultat](media/rsqdicon-refresh.gif "Actualiser les données du résultat")|Actualise les métadonnées à partir de la source de données.|  
|![Ajouter un membre calculé](media/rsqdicon-addcalculatedmember.gif "Ajouter un membre calculé")|Affiche la boîte de dialogue **Générateur de membres calculés** .|  
|![Basculer pour afficher les cellules vides](media/rsqdicon-showemptycells.gif "Basculer pour afficher les cellules vides")|Affiche ou masque les cellules vides dans le volet Données. (Cela revient à utiliser la clause NON EMPTY dans MDX.)|  
|![Exécuter automatiquement la requête](media/rsqdicon-autoexecute.gif "Exécuter automatiquement la requête")|Exécute automatiquement la requête et affiche le résultat chaque fois qu'une modification est effectuée. Les résultats s'affichent dans le volet Données.|  
|![Bouton Afficher les agrégations](media/rsqdicon-showaggregations.gif "Bouton Afficher les agrégations")|Affiche les agrégations dans le volet Données.|  
|![Supprimer](media/rsqdicon-delete.gif "DELETE")|Supprime de la requête la colonne sélectionnée dans le volet Données.|  
|![Icône de la boîte de dialogue Paramètres de la requête](media/iconqueryparameter.gif "Icône de la boîte de dialogue Paramètres de la requête")|Affiche la boîte de dialogue **Paramètres de la requête** . Lorsque vous spécifiez des valeurs pour un paramètre de requête, un paramètre du même nom est automatiquement créé.|  
|![Bouton Préparer la requête](media/rsqdicon-preparequery.gif "Bouton Préparer la requête")|Prépare la requête.|  
|![Exécuter la requête](media/rsqdicon-run.gif "Exécuter la requête")|Exécute la requête et affiche les résultats dans le volet Données.|  
|![Annuler la requête](media/rsqdicon-cancel.gif "Annuler la requête")|Annule la requête.|  
|![Passer en mode Conception](media/rsqdicon-designmode.gif "Passer en mode Création")|Bascule entre le mode Création et le mode Requête.|  
  
## <a name="graphical-mdx-query-designer-in-query-mode"></a>Concepteur de requêtes graphique MDX en mode Requête  
 Pour basculer en mode **Requête** dans le concepteur de requêtes graphique, cliquez sur le bouton bascule **Mode Création** dans la barre d'outils.  
  
 La figure suivante présente les différents volets du mode Requête.  
  
 ![Concepteur de requêtes MDX Analysis Services, mode Requête](media/rsqd-dsawas-mdx-querymode.gif "Concepteur de requêtes MDX Analysis Services, mode Requête")  
  
 Le tableau suivant répertorie les volets disponibles dans ce mode :  
  
|Volet|Fonction|  
|----------|--------------|  
|Bouton Sélection de cube (**...**)|Affiche le cube actuellement sélectionné.|  
|Volet Métadonnées/Fonctions/Modèles|Affiche une liste hiérarchique des mesures, des indicateurs de performance clés (KPI) et des dimensions définis dans le cube sélectionné.|  
|Volet Requête|Affiche le texte de la requête.|  
|Volet Résultat|Affiche les résultats de l'exécution de la requête.|  
  
 Le volet Métadonnées affiche les onglets **Métadonnées**, **Fonctions**et **Modèles**. À partir de l'onglet **Métadonnées** , vous pouvez faire glisser des dimensions, des hiérarchies et des valeurs de performance clés dans le volet Requête MDX. À partir de l'onglet **Fonctions** , vous pouvez faire glisser des fonctions dans le volet Requête MDX. À partir de l'onglet **Modèles** , vous pouvez ajouter des modèles MDX dans le volet Requête MDX. Lorsque vous exécutez la requête, le volet Résultat affiche les résultats pour la requête MDX.  
  
 Vous pouvez étendre la requête MDX par défaut générée en mode Création de façon à inclure des propriétés de membre et de cellule supplémentaires. Lorsque vous exécutez la requête, ces valeurs n'apparaissent pas dans le jeu de résultats. Toutefois, elles sont renvoyées avec la collection de champs de dataset et vous pouvez utiliser ces valeurs.  
  
### <a name="graphical-query-designer-toolbar-in-query-mode"></a>Barre d'outils du concepteur de requêtes graphique en mode Requête  
 La barre d'outils du Concepteur de requêtes fournit des boutons qui vous aident à concevoir des requêtes MDX à l'aide de l'interface graphique.  
  
 Les boutons de la barre d'outils sont identiques en mode Création et en mode Requête, mais les boutons suivants ne sont pas activés en mode Requête :  
  
-   **Modifier en tant que texte**  
  
-   **Ajouter un membre calculé** (![Ajouter un membre calculé](media/rsqdicon-addcalculatedmember.gif "Ajouter un membre calculé"))  
  
-   **Afficher les cellules vides** (![Basculer pour afficher les cellules vides](media/rsqdicon-showemptycells.gif "Basculer pour afficher les cellules vides"))  
  
-   **Exécuter automatiquement** (![Exécuter automatiquement la requête](media/rsqdicon-autoexecute.gif "Exécuter automatiquement la requête"))  
  
-   **Afficher les agrégations** (![Bouton Afficher les agrégations](media/rsqdicon-showaggregations.gif "Bouton Afficher les agrégations"))  
  
  
