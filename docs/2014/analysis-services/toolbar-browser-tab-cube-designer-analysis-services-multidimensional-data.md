---
title: Barre d’outils (onglet navigateur, concepteur de cube) (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a1c6272d-e514-456b-9995-b73fec0112a2
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4d1135be55065ab62e649d84c00cec4eebf60b58
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78175578"
---
# <a name="toolbar-browser-tab-cube-designer-analysis-services---multidimensional-data"></a>Barre d'outils (onglet Explorateur, Concepteur de cube) (Analysis Services - Données multidimensionnelles)
  Utilisez les fonctionnalités de la **Barre d’outils** dans le Concepteur de cube pour exécuter des actions courantes pendant la conception d’un cube, en le parcourant, en parcourant ses objets, ou en créant une requête MDX. Les opérations qui sont communes à la conception et à l'affichage des requêtes incluent la définition du contexte de l'utilisateur, le traitement des objets et la définition de la langue par défaut.

 Le tableau suivant répertorie les boutons de la **Barre d’outils** et leurs fonctions.

|Bouton|Description|
|------------|-----------------|
|**Modifier en tant que texte**|Non activé pour ce type de source de données.|
|**Importer**|Importe une requête existante à partir d'un fichier de définition de rapport (.rdl) sur le système de fichiers.|
|![Basculer vers l'affichage des requêtes DMX](media/rsqdicon-commandtypemdx.gif "Basculer vers l'affichage des requêtes DMX")|Bascule vers le type de commande MDX.|
|![Actualiser les données du résultat](media/rsqdicon-refresh.gif "Actualiser les données du résultat")|Actualise les métadonnées à partir de la source de données.|
|![Ajouter un membre calculé](media/rsqdicon-addcalculatedmember.gif "Ajouter un membre calculé")|Affiche la boîte de dialogue **Générateur de membres calculés** .|
|![Afficher les cellules vides](media/rsqdicon-showemptycells.gif "Afficher les cellules vides")|Affiche ou masque les cellules vides dans le volet Données. (Cela revient à utiliser la clause NON EMPTY dans MDX.)|
|![Exécuter automatiquement la requête](media/rsqdicon-autoexecute.gif "Exécuter automatiquement la requête")|Exécute automatiquement la requête et affiche le résultat chaque fois qu'une modification est effectuée. Les résultats s'affichent dans le volet Données.|
|![Bouton Afficher les agrégations](media/rsqdicon-showaggregations.gif "Bouton Afficher les agrégations")|Affiche les agrégations dans le volet Données.|
|![Supprimer](media/rsqdicon-delete.gif "DELETE")|Supprime de la requête la colonne sélectionnée dans le volet Données.|
|![Icône de la boîte de dialogue Paramètres de la requête](media/iconqueryparameter.gif "Icône de la boîte de dialogue Paramètres de la requête")|Affiche la boîte de dialogue **Paramètres de la requête** . Lorsque vous spécifiez des valeurs pour un paramètre de requête, un paramètre du même nom est automatiquement créé.|
|![Bouton Préparer la requête](media/rsqdicon-preparequery.gif "Bouton Préparer la requête")|Prépare la requête.|
|![Exécuter la requête](media/rsqdicon-run.gif "Exécuter la requête")|Exécute la requête et affiche les résultats dans le volet Données.|
|![Annuler la requête](media/rsqdicon-cancel.gif "Annuler la requête")|Annule la requête.|
|![Passer en mode création](media/rsqdicon-designmode.gif "Passer en mode Création")|Bascule entre le mode Création et le mode Requête.|

 En général les boutons de la barre d’outils sont les mêmes pour le mode **Création** et **Requête**. Toutefois, les boutons suivants ne sont pas activés en mode Requête :

-   **Modifier en tant que texte**

-   **Ajouter un membre calculé** (![Ajouter un membre calculé](media/rsqdicon-addcalculatedmember.gif "Ajouter un membre calculé"))

-   **Afficher les cellules vides** (afficher![/Masquer les cellules vides](media/rsqdicon-showemptycells.gif "Afficher les cellules vides"))

-   **Exécution** automatique (![exécution automatique de la requête](media/rsqdicon-autoexecute.gif "Exécuter automatiquement la requête"))

-   **Afficher les agrégations** (![bouton afficher les agrégations](media/rsqdicon-showaggregations.gif "Bouton Afficher les agrégations"))

## <a name="options"></a>Options

|Option|Description|
|------------|-----------------|
|**Traiter**|Cliquez pour afficher la boîte de dialogue **Traiter** et traiter le cube. Pour plus d’informations sur la boîte de dialogue **Traiter**, consultez [Boîte de dialogue Traiter &#40;Analysis Services - Données multidimensionnelles&#41;](process-dialog-box-analysis-services-multidimensional-data.md).|
|**Changer d'utilisateur**|Cliquez pour afficher la boîte de dialogue **contexte de sécurité** et modifier l’utilisateur et le rôle utilisés sous l’onglet **navigateur** . Pour plus d’informations sur la boîte de dialogue **contexte de sécurité** , consultez [boîte de dialogue contexte de sécurité &#40;Analysis Services-données multidimensionnelles&#41;](security-context-dialog-box-analysis-services-multidimensional-data.md).|
|**Reconnexion**|Permet de reconnecter l’onglet **Calculs** à l’instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] et à la base de données qui contient le cube, si la session correspondant à l’onglet **Navigateur** est déconnectée à cause de la perte de la connexion ou de l’expiration de cette dernière.|
|**Actualiser**|Permet d’actualiser les volets **Métadonnées** et **Rapports** .|
|**Tri croissant**|Permet de trier les frères de la ligne sélectionnée dans le volet **Rapport** en ordre ascendant et selon la langue précisée dans **Langue**.<br /><br /> **Remarque** Cette option est activée uniquement si une cellule du volet **rapports** est sélectionnée.|
|**Tri décroissant**|Permet de trier les frères de la ligne sélectionnée dans le volet **Rapport** en ordre descendant et selon la langue précisée dans **Langue**.<br /><br /> Remarque : Cette option n’est activée que si une cellule du volet **Rapports** est sélectionnée.|
|**Filtre automatique**|Lance le filtre automatiquement sur les résultats du volet **Résultat** .|
|**Afficher seulement le haut/bas**|Permet de choisir une valeur ou un pourcentage afin de n’afficher que les cellules répondant au critère du nombre ou du pourcentage maximal/minimal indiqué, dans le volet **Rapport** et selon la mesure choisie.<br /><br /> Pour plus d’informations sur cette option, consultez [TopCount &#40;MDX&#41;](/sql/mdx/topcount-mdx), [TopPercent &#40;MDX&#41;](/sql/mdx/toppercent-mdx), [BottomCount &#40;MDX&#41;](/sql/mdx/bottomcount-mdx) et [BottomPercent &#40;MDX&#41;](/sql/mdx/bottompercent-mdx).|
|**Sous**|Permet d'afficher les sous-totaux.|
|**Totaux de tous les éléments**|Permet d’afficher les totaux de Tous les membres du volet **Rapport** .|
|**Afficher les cellules vides**|Permet d’afficher les cellules vides dans le volet **Rapport** .|
|**Effacer les résultats**|Permet d’effacer les résultats du volet **apport** .|
|**Commandes et options**|Permet d’afficher la boîte de dialogue **Commandes et options** et de modifier les propriétés avancées du contrôle de tableau croisé dynamique Microsoft Office 11.0 PivotTable dans le volet **Rapport** . Pour de plus amples informations à propos de la boîte de dialogue **Commandes et options** , consultez la documentation de Microsoft Office.|
|**Perspective**|Permet de sélectionner la perspective d’affichage des données et des métadonnées dans les volets **Métadonnées** et **Rapport** .<br /><br /> Pour afficher le cube mais sans utiliser de perspective, sélectionnez dans ce cas le nom du cube.|
|**Langage**|Permet de sélectionner la langue d’affichage des données et des métadonnées dans les volets **Métadonnées** et **Rapport** .<br /><br /> Pour afficher le cube mais sans utiliser de perspective, sélectionnez dans ce cas **Par défaut**.|


