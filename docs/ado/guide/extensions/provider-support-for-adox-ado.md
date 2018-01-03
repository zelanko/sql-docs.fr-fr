---
title: Prise en charge de fournisseur pour ADOX (ADO) | Documents Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ADOX provider support [ADO]
ms.assetid: 64234ce5-dc46-4c8a-a316-61956b6b9abb
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 807d82796227187fc35c97896819e5cedca9fd14
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="provider-support-for-adox-ado"></a>Prise en charge de fournisseur pour ADOX (ADO)
Certaines fonctionnalités d’ADOX ne sont pas pris en charge, en fonction de votre fournisseur de données OLE DB. ADOX est entièrement compatible avec le [fournisseur OLE DB pour Microsoft Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md). Les fonctionnalités non prises en charge avec la [fournisseur Microsoft OLE DB pour SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md), le [fournisseur Microsoft OLE DB pour ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md), ou [fournisseur Microsoft OLE DB pour Oracle](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-oracle.md) sont répertoriées dans les tableaux suivants. ADOX n’est pas pris en charge par tous les autres fournisseurs OLE DB de Microsoft.  
  
## <a name="microsoft-ole-db-provider-for-sql-server"></a>Fournisseur Microsoft OLE DB pour SQL Server  
  
|Objet ou la Collection|Restriction d’utilisation|  
|--------------------------|-----------------------|  
|**Tables** collection|Propriétés sont en lecture/écriture avant de créer un objet et en lecture seule lors du référencement d’un objet existant.|  
|**Vues** collection|**Vues** n’est pas pris en charge.|  
|**Procédures** collection|Le **Append** et **supprimer** méthodes ne sont pas prises en charge.|  
|**Procédure** objet|Le **commande** propriété n’est pas prise en charge.|  
|**Clés** collection|Le **Append** et **supprimer** méthodes ne sont pas prises en charge.|  
|**Les utilisateurs** collection|**Les utilisateurs** n’est pas pris en charge.|  
|**Groupes** collection|**Groupes** n’est pas pris en charge.|  
  
## <a name="microsoft-ole-db-provider-for-odbc"></a>Fournisseur Microsoft OLE DB pour ODBC  
  
|Objet ou la Collection|Restriction d’utilisation|  
|--------------------------|-----------------------|  
|**Catalogue** objet|Le **créer** méthode n’est pas prise en charge.|  
|**Tables** collection|Le **Append** et **supprimer** méthodes ne sont pas prises en charge. Propriétés sont en lecture/écriture avant de créer un objet et en lecture seule lors du référencement d’un objet existant.|  
|**Procédures** collection|Le **Append** et **supprimer** méthodes ne sont pas prises en charge.|  
|**Procédure** objet|Le **commande** propriété n’est pas prise en charge.|  
|**Index** collection|Le **Append** et **supprimer** méthodes ne sont pas prises en charge.|  
|**Clés** collection|Le **Append** et **supprimer** méthodes ne sont pas prises en charge.|  
|**Les utilisateurs** collection|**Les utilisateurs** n’est pas pris en charge.|  
|**Groupes** collection|**Groupes** n’est pas pris en charge.|  
  
## <a name="microsoft-ole-db-provider-for-oracle"></a>Fournisseur Microsoft OLE DB pour Oracle  
  
|Objet ou la Collection|Restriction d’utilisation|  
|--------------------------|-----------------------|  
|**Catalogue** objet|Le **créer** méthode n’est pas prise en charge.|  
|**Tables** collection|Le **Append** et **supprimer** méthodes ne sont pas prises en charge. Propriétés sont en lecture/écriture avant de créer un objet et en lecture seule lors du référencement d’un objet existant.|  
|**Vues** collection|Le **Append** et **supprimer** méthodes ne sont pas prises en charge.|  
|**Vue** objet|Le **commande** propriété n’est pas prise en charge.|  
|**Procédures** objet|Le **Append** et **supprimer** méthodes ne sont pas prises en charge.|  
|**Procédure** objet|Le **commande** propriété n’est pas prise en charge.|  
|**Index** collection|Le **Append** et **supprimer** méthodes ne sont pas prises en charge.|  
|**Clés** collection|Le **Append** et **supprimer** méthodes ne sont pas prises en charge.|  
|**Les utilisateurs** collection|**Les utilisateurs** n’est pas pris en charge.|  
|**Groupes** collection|**Groupes** n’est pas pris en charge.|
