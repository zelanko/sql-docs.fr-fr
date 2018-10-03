---
title: Accès aux fichiers utilisés par les Packages | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS packages, security
- packages [Integration Services], security
- configuration files [Integration Services]
- checkpoint files
- Integration Services packages, security
- logs [Integration Services], security
- files [Integration Services], security
- SQL Server Integration Services packages, security
ms.assetid: 2e3ddea9-5289-4289-a70e-11c018f34977
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6b6e78e04a64f9bddeeb4f24ba2f90919b9d228c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48214989"
---
# <a name="access-to-files-used-by-packages"></a>Accéder aux fichiers utilisés par des packages
  Le niveau de protection de package ne protège pas les fichiers stockés en dehors du package. Il s'agit des fichiers suivants :  
  
-   Fichiers de configuration  
  
-   fichiers de point de contrôle  
  
-   Fichiers journaux  
  
 Ces fichiers doivent être protégés séparément, notamment s'ils contiennent des informations sensibles.  
  
## <a name="configuration-files"></a>Fichiers de configuration  
 Si une configuration contient des informations sensibles, telles que des informations de connexion et de mot de passe, vous devez penser à enregistrer la configuration dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], ou à utiliser une liste de contrôle d’accès pour limiter l’accès à l’emplacement ou au dossier de stockage des fichiers et pour autoriser l’accès uniquement à certains comptes. En règle générale, vous accordez l'accès aux comptes que vous autorisez à exécuter des packages et à ceux qui gèrent et résolvent les problèmes des packages, ce qui peut comprendre l'inspection du contenu des fichiers de configuration, des fichiers de point de contrôle et des fichiers journaux. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] fournit le stockage le plus sécurisé, car il offre une protection aux niveaux du serveur et des bases de données. Pour enregistrer des configurations dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], vous utilisez le type de configuration [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Pour enregistrer dans le système de fichiers, vous utilisez le type de configuration XML.  
  
 Pour plus d’informations, consultez [Configurations de package](../../2014/integration-services/package-configurations.md), [Créer des configurations de package](../../2014/integration-services/create-package-configurations.md)et [Considérations sur la sécurité pour une installation SQL Server](../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md).  
  
## <a name="checkpoint-files"></a>fichiers de point de contrôle  
 De même, si le fichier de point de contrôle utilisé par le package contient des informations sensibles, vous devez utiliser une liste de contrôle d'accès pour sécuriser l'emplacement ou le dossier de stockage du fichier. Les fichiers de points de contrôle contiennent des informations d'état relatives à la progression du package, ainsi que les valeurs actuelles de certaines variables. Par exemple, le package peut inclure une variable personnalisée qui contient un numéro de téléphone. Pour plus d'informations, consultez [Redémarrer des packages à l'aide de points de contrôle](packages/restart-packages-by-using-checkpoints.md).  
  
## <a name="log-files"></a>Fichiers journaux  
 Les entrées de journaux qui sont écrites dans le système de fichiers doivent également être sécurisées au moyen d'une liste de contrôle d'accès. Elles peuvent aussi être stockées dans des tables [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et protégées par la sécurité [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Les entrées de journaux peuvent inclure des informations sensibles. Par exemple, si le package contient une tâche d'exécution SQL qui construit une instruction SQL faisant référence à un numéro de téléphone, l'entrée de journal de l'instruction SQL inclut le numéro de téléphone. L'instruction SQL peut également révéler des informations confidentielles relatives à des noms de tables et de colonnes dans des bases de données. Pour plus d’informations, consultez [Journalisation Integration Services &#40;SSIS&#41;](performance/integration-services-ssis-logging.md).  
  
  
