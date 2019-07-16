---
title: Paramètres (synchronisation) (SybaseToSQL) du projet | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 2cd6bc01-b8e5-4312-83a4-eac66dc1d460
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 663a4b1e49d1f81ce040254a2c8f39a1a1f84b38
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68028683"
---
# <a name="project-settings-synchronization-sybasetosql"></a>Paramètres du projet (Synchronisation) (SybaseToSQL)
La page de synchronisation de la **paramètres du projet** boîte de dialogue contient les paramètres qui personnalisent comment SSMA charge les objets de base de données, telles que les tables et procédures stockées, dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure.  
  
Vous pouvez accéder à deux différentes pages de synchronisation qui contiennent les mêmes paramètres :  
  
-   Si vous souhaitez spécifier des paramètres pour tous les futurs projets SSMA, sur le **outils** menu, sélectionnez **par défaut des paramètres de projet**, sélectionnez le type de projet de migration pour lequel les paramètres sont requis pour être affichées ou modifiées à partir de **Version cible de Migration** liste déroulante, puis sélectionnez **synchronisation** en bas du volet gauche.  
  
-   Pour spécifier les paramètres pour le projet actuel, sur le **outils** menu, sélectionnez **paramètres du projet**, puis sélectionnez **synchronisation** en bas du volet gauche.  
  
## <a name="options"></a>Options  
**Tentatives**  
Spécifie le nombre de tentatives de SSMA doit lors du chargement d’objets dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les objets qui ne sont pas chargés dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lors de la tentative actuelle sera tentée à nouveau jusqu'à ce que SSMA atteigne le nombre maximal de tentatives défini dans le processus de synchronisation en cours.  
  
## <a name="synchronization-for-sql-server"></a>Synchronisation pour SQL Server  
**Actualiser l’objet local sur la modification de l’objet locaux et distants**  
Spécifie si SSMA doit remplacer les métadonnées de l’objet local avec les métadonnées de l’objet distant si vous modifient les objets locaux et distants.  
Si vous sélectionnez **Actualiser à partir de la base de données**, SSMA chargera les définitions de base de données dans les métadonnées lorsque la condition est remplie.  
Si vous sélectionnez **écrire dans la base de données**, SSMA met à jour les objets dans la base de données en fonction du contenu des métadonnées SSMA lorsque la condition est remplie.  
Si vous sélectionnez **Skip**, SSMA n’effectuera pas les actions d’actualisation.   
Groupe d’options par défaut est **écrire dans la base de données.**  
  
**Actualiser l’objet local sur la modification de l’objet local**  
Spécifie si SSMA doit remplacer les métadonnées de l’objet local avec les métadonnées de l’objet distant si l’objet distant est modifié.  
Si vous sélectionnez **Actualiser à partir de la base de données**, SSMA chargera les définitions de base de données dans les métadonnées lorsque la condition est remplie.  
Si vous sélectionnez **écrire dans la base de données**, SSMA met à jour l’objet dans la base de données en fonction du contenu des métadonnées SSMA lorsque la condition est remplie.  
Si vous sélectionnez **Skip**, SSMA n’effectuera pas les actions d’actualisation.   
Groupe d’options par défaut est **écrire dans la base de données**.  
  
**Actualiser l’objet local sur la modification de l’objet distant**  
Spécifie si SSMA doit remplacer les métadonnées de l’objet local avec les métadonnées de l’objet distant si l’objet distant est modifié.  
Si vous sélectionnez **Actualiser à partir de la base de données**, SSMA chargera les définitions de base de données dans les métadonnées lorsque la condition est remplie.  
Si vous sélectionnez **écrire dans la base de données**, SSMA met à jour l’objet dans la base de données en fonction du contenu des métadonnées SSMA lorsque la condition est remplie.  
Si vous sélectionnez **Skip**, SSMA n’effectuera pas les actions d’actualisation.   
Groupe d’options par défaut est **Actualiser à partir de la base de données**.  
  
**Actualisation des métadonnées de l’objet local sont manquante**  
Spécifie si SSMA doit créer les métadonnées locales si un objet existe sur la base de données cible, mais pas localement.  
Si vous sélectionnez **Actualiser à partir de la base de données**, SSMA sélectionne l’actualisation à partir de l’option de base de données lorsque la condition est remplie.  
Si vous sélectionnez **écrire dans la base de données**, SSMA supprimera l’objet à partir de la base de données lorsque la condition est remplie.  
Si vous sélectionnez **Skip**, SSMA n’effectuera pas les actions d’actualisation.   
Groupe d’options par défaut est **Actualiser à partir de la base de données**.  
  
