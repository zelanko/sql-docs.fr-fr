---
title: Journal des modifications pour SQL Server Reporting Services (SSRS) 2017 et versions ultérieures | Microsoft Docs
ms.date: 08/31/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
author: casualoak
ms.author: RhysSchmidtke
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 0eec59b0d2618686f866e6b7799922d9c255b238
ms.sourcegitcommit: 009bee6f66142c48477849ee03d5177bcc3b6380
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56230906"
---
# <a name="change-log-for-sql-server-reporting-services-ssrs-2017-and-later"></a>Journal des modifications pour SQL Server Reporting Services (SSRS) 2017 et versions ultérieures

[!INCLUDE [ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2017-and-later](../includes/ssrs-appliesto-2017-and-later.md)] 

Cet article décrit les modifications apportées dans [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. 

## <a name="sql-server-2017-reporting-services"></a>SQL Server 2017 Reporting Services 

### <a name="version-1406001109-released-february-12-2019"></a>Version 14.0.600.1109, Date de publication : 12 février 2019

Les problèmes suivants ont été résolus :

 - Les planification des captures instantanées de rapport de cache devient « planification spécifique aux rapports » après modification de l’abonnement.
 - rc:Toolbar=false ne fonctionne pas dans l’édition Express.
 - Certains caractères thaïs sont mal restitués à l’exportation de rapports paginés au format PDF.
 - Un blocage se produit lors de la notification de fin des abonnements pilotés par les données.
 - Les images incorporées ne s’affichent pas dans certaines circonstances, lorsque le paramètre rc:Toolbar=False est utilisé.
 - Il n’est pas possible de créer des abonnements pilotés par les données pour les rapports qui utilisent des paramètres en cascade.
 - Il n’est pas possible de modifier les abonnements configurés avec un intervalle non valide.
 - Mises à jour de sécurité
 - L’interface utilisateur des rapports liés ne s’affiche pas.
 - Certains rapports paginés comportant des contrôles de tableau matriciel imbriqué présentent des polices incorrectes.
 - Un espace blanc est ajouté à tort à certains rapports paginés contenant des régions de données de tableau matriciel.
 - Les lignes d’en-tête disparaissent en cas de développement des grilles de données simples de rapports mobiles.

### <a name="version-140600906-released-september-12-2018"></a>Version 14.0.600.906, Date de publication : 12 septembre 2018

Le problème suivant a été résolu :

- L’authentification personnalisée ne renvoie pas les informations correctes relatives aux cookies

### <a name="version-140600892-released-august-31-2018"></a>Version 14.0.600.892, Date de publication : 31 août 2018

Les problèmes suivants ont été résolus :

- À cause de la zone de texte dans le rectangle, celui-ci ne peut pas s’agrandir verticalement quand rc:Toolbar=False et que le texte est long 
- La taille du texte n’est pas évolutive si pageHeight est inférieur à 0,5 po 
- Interblocage dans la base de données du catalogue SSRS en cas d’utilisation avec CRM 
- Les en-têtes de colonne alignés verticalement s’affichent incorrectement lors du défilement vers le bas dans le rapport 
- Les utilisateurs ajoutés au rôle de création de rapports SCOM ne peuvent pas accéder au portail web SSRS 
- Un caractère thaïlandais n’est pas correctement exporté au format PDF 
- Changement de comportement du rôle du navigateur 
- rc:Toolbar=false ne fonctionne pas dans les éditions Express 
- Barre de défilement verticale manquante dans la zone de message du paramètre 
- Runtime de rapport mobile mis à jour 

### <a name="version-140600744-released-april-25-2018"></a>Version 14.0.600.744, Date de publication : 25 avril 2018 

Les problèmes suivants ont été résolus :

- La page Abonnement contrôlé par les données n’affiche pas l’option de remise qui a été créée
- La mise à niveau de SSRS 2012 avec SSRS 2017 dans RSManagement génère une exception toutes les deux ou trois secondes
- Impossible de modifier les valeurs par défaut pour les paramètres à valeurs multiples dans IE11
- Les planifications sont vides chaque fois qu’une planification partagée est exécutée

### <a name="version-140600689-released-february-28-2018"></a>Version 14.0.600.689, Date de publication : 28 février 2018

Les problèmes suivants ont été résolus :

- La visibilité de Paramètre de rapport dans un rapport lié est rétablie après la modification de ses propriétés
- Le paramètre d’URL rc:Toolbar=false ne fonctionne pas dans les éditions Express
- Les valeurs ne s’affichent pas en cas de présence d’expressions dans la zone de texte avec la propriété CanGrow définie sur false
- Lien « En savoir plus » ajouté pour la clé de produit dans le programme d’installation
- Le portail web avec l’authentification par formulaires personnalisée ignore le cookie d’expiration décalé
- L’exportation vers Word crée une hauteur de ligne inégale si le contenu de la ligne est vide

### <a name="version-140600594-released-january-9-2018"></a>Version 14.0.600.594, Date de publication : 9 janvier 2018

Mises à jour de sécurité

### <a name="version-140600490-released-november-1-2017"></a>Version 14.0.600.490, Date de publication : 1er novembre 2017

Les problèmes suivants ont été résolus :

- Problèmes résolus avec la mise à niveau de la référence (SKU)

### <a name="version-140600451-released-september-30-2017"></a>Version 14.0.600.451, Date de publication : 30 septembre 2017 

Version initiale

## <a name="next-steps"></a>Étapes suivantes

[Nouveautés de Reporting Services (SSRS)](what-s-new-in-sql-server-reporting-services-ssrs.md)   

D’autres questions ? [Essayez de poser une question dans le forum Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231)
