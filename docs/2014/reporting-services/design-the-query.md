---
title: Concevoir la requête | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptwizard.designquery.f1
ms.assetid: 2dad800f-10a1-453c-8761-2935b9826d84
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 4aaea45ff2059564bf2215aa4728dee80e4539b3
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56298397"
---
# <a name="design-the-query"></a>Concevoir la requête
  Utilisez cette page de l'Assistant Rapport pour créer une requête en la tapant manuellement, en utilisant le Générateur de requêtes pour créer une requête de manière interactive ou en important une requête à partir d'un autre rapport.  
  
 Le type de source de données sélectionné dans la page Sélectionner la source de données, à la page précédente de l'Assistant Rapport, détermine la requête que vous pouvez spécifier dans cette page. Par exemple, si le type de source de données est [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], vous pouvez entrer des instructions [!INCLUDE[tsql](../includes/tsql-md.md)] ou des noms de procédures stockées. Si le type de source de données est [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], le volet Requête est désactivé et vous ne pouvez pas entrer de requête directement. Vous pouvez spécifier la requête en utilisant le Générateur de requêtes.  
  
## <a name="options"></a>Options  
 **Chaîne de requête**  
 Tapez une requête qui extrait les données que vous voulez utiliser dans votre rapport.  
  
 **Générateur de requêtes**  
 Cliquez sur **Générateur de requêtes** pour ouvrir un concepteur de requêtes pour la source de données ou pour importer une requête à partir d’un autre rapport.  
  
 Pour plus d'informations sur les concepteurs de requêtes, consultez [Reporting Services Query Designers](../../2014/reporting-services/reporting-services-query-designers.md).  
  
## <a name="example"></a>Exemple  
 Pour le type de source de données **Microsoft SQL Server**, la requête suivante récupère une liste des noms depuis le [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] base de données `Person` table.  
  
```  
SELECT LastName FROM Person.Person;  
```  
  
 Pour le type de source de données **Microsoft SQL Server**, la requête suivante exécute la [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] procédure stockée `uspGetEmployeeManagers` pour l’employé avec identification numéro 1 :  
  
```  
EXEC uspgetEmployeeManagers '1';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Aide de l’Assistant rapport](../../2014/reporting-services/report-wizard-help.md)   
 [Datasets incorporés dans le rapport et datasets partagés &#40;Générateur de rapports et SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Ajouter des données à un rapport &#40;Générateur de rapports et SSRS&#41;](report-data/report-datasets-ssrs.md)  
  
  
