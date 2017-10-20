---
title: Catalog.check_schema_version | Documents Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: e0d5e9f5-59c6-4118-87b5-4aa5c37a7df6
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 56eacb6ed209f34f65ae406fe4dd520284b79e5b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogcheckschemaversion"></a>catalog.check_schema_version
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Détermine si le schéma de catalogue SSISDB et les binaires [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] (assembly ISServerExec et SQLCLR) sont compatibles.  
  
 ISServerExec.exc enregistre un message d'erreur lorsque le schéma et les fichiers binaires sont incompatibles.  
  
 La version du schéma SSISDB est incrémentée quand le schéma change lors de l'application des correctifs logiciels et lors des mises à niveau. Il est recommandé d'exécuter cette procédure stockée après qu'une sauvegarde SSISDB a été restaurée afin de garantir que le schéma et les fichiers binaires sont compatibles.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
catalog.check_schema_version [@use32bitruntime = ] use32bitruntime  
```  
  
## <a name="arguments"></a>Arguments  
 [ @use32bitruntime=] *use32bitruntime*  
 Lorsque le paramètre a la valeur **True**, la version 32 bits de dtexec est appelée. Le *use32bitruntime* est un **Bool**.  
  
## <a name="result-set"></a>Jeu de résultats  
 Aucune  
  
## <a name="permissions"></a>Permissions  
 Cette procédure stockée requiert l'autorisation suivante :  
  
-   L’appartenance à la **ssis_admin** rôle de base de données.  
  
  
