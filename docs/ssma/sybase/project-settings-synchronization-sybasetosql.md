---
title: Paramètres du projet (synchronisation) (SybaseToSQL) | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68028683"
---
# <a name="project-settings-synchronization-sybasetosql"></a>Paramètres du projet (Synchronisation) (SybaseToSQL)
La page synchronisation de la boîte de dialogue **paramètres du projet** contient des paramètres qui personnalisent la manière dont SSMA charge les objets de base de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données, tels que les tables et les procédures stockées, dans ou SQL Azure.  
  
Vous pouvez accéder à deux pages de synchronisation différentes qui contiennent les mêmes paramètres :  
  
-   Si vous souhaitez spécifier des paramètres pour tous les futurs projets SSMA, dans le menu **Outils** , sélectionnez **paramètres du projet par défaut**, sélectionnez le type de projet de migration pour lequel les paramètres doivent être affichés ou modifiés dans la liste déroulante de la **version cible** de la migration, puis sélectionnez **synchronisation** en bas du volet gauche.  
  
-   Pour spécifier les paramètres du projet actif, dans le menu **Outils** , sélectionnez **paramètres du projet**, puis sélectionnez **synchronisation** en bas du volet gauche.  
  
## <a name="options"></a>Options  
**Essayer**  
Spécifie le nombre de tentatives que SSMA doit effectuer lors du chargement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]des objets dans. Les objets qui ne sont pas [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] chargés dans la tentative actuelle seront tentés à nouveau jusqu’à ce que SSMA atteigne le nombre maximal de tentatives dans le processus de synchronisation en cours.  
  
## <a name="synchronization-for-sql-server"></a>Synchronisation pour SQL Server  
**Actualiser l’objet local sur la modification de l’objet local et distant**  
Spécifie si SSMA doit remplacer les métadonnées de l’objet local par les métadonnées de l’objet distant si les objets locaux et distants changent.  
Si vous sélectionnez **Actualiser à partir de la base de données**, SSMA chargera les définitions de base de données dans les métadonnées lorsque la condition est remplie.  
Si vous sélectionnez **écrire dans la base de données**, SSMA met à jour les objets dans la base de données en fonction du contenu des métadonnées SSMA lorsque la condition est remplie.  
Si vous sélectionnez **Ignorer**, SSMA n’effectue aucune action d’actualisation.   
L’option par défaut est **écrire dans la base de données.**  
  
**Actualiser l’objet local lors de la modification de l’objet local**  
Spécifie si SSMA doit remplacer les métadonnées de l’objet local par les métadonnées de l’objet distant si l’objet distant est modifié.  
Si vous sélectionnez **Actualiser à partir de la base de données**, SSMA chargera les définitions de base de données dans les métadonnées lorsque la condition est remplie.  
Si vous sélectionnez **écrire dans la base de données**, SSMA met à jour l’objet dans la base de données en fonction du contenu des métadonnées SSMA lorsque la condition est remplie.  
Si vous sélectionnez **Ignorer**, SSMA n’effectue aucune action d’actualisation.   
L’option par défaut est **écrire dans la base de données**.  
  
**Actualiser l’objet local lors de la modification de l’objet distant**  
Spécifie si SSMA doit remplacer les métadonnées de l’objet local par les métadonnées de l’objet distant si l’objet distant est modifié.  
Si vous sélectionnez **Actualiser à partir de la base de données**, SSMA chargera les définitions de base de données dans les métadonnées lorsque la condition est remplie.  
Si vous sélectionnez **écrire dans la base de données**, SSMA met à jour l’objet dans la base de données en fonction du contenu des métadonnées SSMA lorsque la condition est remplie.  
Si vous sélectionnez **Ignorer**, SSMA n’effectue aucune action d’actualisation.   
L’option par défaut est **Actualiser à partir de la base de données**.  
  
**Actualiser lorsque les métadonnées de l’objet local sont manquantes**  
Spécifie si SSMA doit créer des métadonnées locales si un objet existe dans la base de données cible, mais pas localement.  
Si vous sélectionnez **Actualiser à partir de la base de données**, SSMA sélectionne l’option Actualiser à partir de la base de données lorsque la condition est remplie.  
Si vous sélectionnez **écrire dans la base de données**, SSMA supprime l’objet de la base de données lorsque la condition est remplie.  
Si vous sélectionnez **Ignorer**, SSMA n’effectue aucune action d’actualisation.   
L’option par défaut est **Actualiser à partir de la base de données**.  
  
