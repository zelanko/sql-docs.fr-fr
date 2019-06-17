---
title: Notes de publication pour (SSRS) 2017 et versions ultérieures | Microsoft Docs
ms.date: 02/18/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.reviewer: maggies
author: casualoak
ms.author: rhys
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions'
ms.openlocfilehash: cd2f9dec39075b332b2ae38c622f3970faf8d331
ms.sourcegitcommit: c40f663d4486e574fd749f2c8e84c98d41970352
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67037850"
---
# <a name="release-notes-for-sql-server-reporting-services-ssrs-2017-and-later"></a>Notes de publication de SQL Server Reporting Services (SSRS) 2017 et versions ultérieures

[!INCLUDE [ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2017-and-later](../includes/ssrs-appliesto-2017-and-later.md)]

Cet article décrit les modifications apportées à [!INCLUDE[ssnoversion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (SSRS), pour les versions 2017 et versions ultérieures.

Pour les notes de publication pour les contrôles de visionneuse de rapports, consultez [contrôle des Notes de publication pour la visionneuse de rapports pour Web Forms et WinForms de SSRS](application-integration/release-notes-ssrs-application-integration.md).

<!--
We are "standardizing" all our 'Release Notes' style articles:

  - File names:   'release-notes-[TechArea-Name].md'


  - Content format:   2-column tables.  No longer using bullet lists.

    - Ideally, the 'Details' column should contain a link to another SSRS documentation article wherein the particular issue fix is discussed in any way.  Or if there is more to say beyond one sentence, the other sentences of elaboration would go into the 'Details' column.


  - H2 header names are kept short, for better display.


  - Try to keep all Release Notes in one .md file.  Avoid having multiple R.N. files whose names differ only by version or date.

    - Seriously consider erasing info about ancient releases that are so old that nobody cares about them anymore.  If you really want to retain ancient info, consider doing so in an HTML comment at the end of the .md file, just in case a Microsoft employee needs to re-examine ancient info.  In any case, this file cannot get ever longer, and some deletion or hiding of oldest info must eventually occur.


  - Do use '::: moniker range=' zones when version 2017 is no longer the only version represented inside this .md file.

    - Use the '=' operator on the moniker, not the '>=' operator.
    - In contrast, in our 'Whats New' articles we do use the '>=', rather than '='.

GeneMi, DevOps = 1467988 (MsEng > TechnicalContent) , 2019/03/19
-->

## <a name="1406001109-20190212"></a>14.0.600.1109, 12/02/2019

| Résolution du problème | Détails |
| :---------- | :------ |
| Les planification des captures instantanées de rapport de cache devient « planification spécifique aux rapports » après modification de l’abonnement. | &nbsp; |
| rc:Toolbar=false ne fonctionne pas dans Express Edition. | &nbsp; |
| Certains caractères thaïs sont mal restitués à l’exportation de rapports paginés au format PDF. | &nbsp; |
| Un blocage se produit lors de la notification de fin des abonnements pilotés par les données. | &nbsp; |
| Les images incorporées ne s’affichent pas dans certaines circonstances, lorsque le paramètre rc:Toolbar=False est utilisé. | &nbsp; |
| Il n’est pas possible de créer des abonnements pilotés par les données pour les rapports qui utilisent des paramètres en cascade. | &nbsp; |
| Il n’est pas possible de modifier les abonnements configurés avec un intervalle non valide. | &nbsp; |
| Mises à jour de sécurité. | &nbsp; |
| L’interface utilisateur des rapports liés ne s’affiche pas. | &nbsp; |
| Certains rapports paginés comportant des contrôles de tableau matriciel imbriqué présentent des polices incorrectes. | &nbsp; |
| Espace blanc est correctement ajouté à certains des rapports paginés qui contiennent des régions de données de tableau matriciel. | &nbsp; |
| Les lignes d’en-tête disparaissent en cas de développement des grilles de données simples d’un rapport mobile. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="140600906-20180912"></a>14.0.600.906, 12/09/2018

Le problème suivant a été résolu :

| Résolution du problème | Détails |
| :---------- | :------ |
| L’authentification personnalisée ne renvoie pas les bonnes informations sur les cookies. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="140600892-20180831"></a>14.0.600.892, 31/08/2018

| Résolution du problème | Détails |
| :---------- | :------ |
| À cause de la zone de texte dans le rectangle, celui-ci ne peut pas s’agrandir verticalement quand rc:Toolbar=False et que le texte est long. | &nbsp; |
| La taille du texte ne s’adapte pas si pageHeight est inférieur à 0,5 pouce. | &nbsp; |
| Un blocage se produit dans la base de données du catalogue SSRS lorsqu’il est utilisé avec CRM. | &nbsp; |
| Les en-têtes de colonne alignés verticalement s’affichent mal lors du défilement vers le bas dans un rapport. | &nbsp; |
| Les utilisateurs ajoutés au rôle de création de rapports de System Center Operations Manager ont accès bloqué au portail web SSRS. | &nbsp; |
| Caractères thaïlandais n’est pas été correctement exportés dans le fichier PDF. | &nbsp; |
| Changement de comportement du rôle Visiteur. | &nbsp; |
| rc:Toolbar=false ne fonctionne pas dans Express Edition. | &nbsp; |
| Manquant dans la barre de défilement verticale dans la zone de message du paramètre. | &nbsp; |
| Runtime de rapport mobile mis à jour. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="140600744-20180425"></a>14.0.600.744, 25/04/2018

| Résolution du problème | Détails |
| :---------- | :------ |
| La page Abonnement piloté par les données n’affiche pas l’option de livraison qui a été créée. | &nbsp; |
| En cas de mise à niveau de SSRS 2012 vers SSRS 2017, RSManagement génère une exception toutes les deux ou trois secondes. | &nbsp; |
| Il n’est pas possible de modifier les valeurs par défaut des paramètres à valeurs multiples dans IE11. | &nbsp; |
| Les planifications sont vides chaque fois qu’une planification partagée est exécutée. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="140600689-20180228"></a>14.0.600.689, 28/02/2018

| Résolution du problème | Détails |
| :---------- | :------ |
| La visibilité de Paramètre de rapport dans un rapport lié est rétablie après modification de ses propriétés. | &nbsp; |
| Le paramètre d’URL rc:Toolbar=false ne fonctionne pas dans Express Edition. | &nbsp; |
| Présence d’expressions dans une zone de texte avec le CanGrow propriété la valeur false entraîne des valeurs s’affichent ne pas. | &nbsp; |
| Le lien _En savoir plus_ est ajouté pour la clé de produit dans le programme d’installation. | &nbsp; |
| Le portail web avec l’authentification par formulaires personnalisée ignore le cookie à expiration décalé. | &nbsp; |
| L’exportation dans Word crée une hauteur de ligne inégale si le contenu de la ligne est vide. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="140600594-20180109"></a>14.0.600.594, 09/01/2018

Certaines mises à jour de sécurité ont été implémentées.

### <a name="140600490-20171101"></a>14.0.600.490, 01/11/2017

Les problèmes de mise à niveau des références SKU sont résolus.

## <a name="140600451-20170930"></a>14.0.600.451, 30/09/2017

Version initiale.

## <a name="next-steps"></a>Étapes suivantes

[Nouveautés de Reporting Services (SSRS)](what-s-new-in-sql-server-reporting-services-ssrs.md)

D’autres questions ? [Posez une question dans le forum Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
