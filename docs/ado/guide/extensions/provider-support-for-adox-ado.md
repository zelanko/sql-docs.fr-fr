---
description: Prise en charge de fournisseur pour ADOX (ADO)
title: Prise en charge du fournisseur pour ADOX (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADOX provider support [ADO]
ms.assetid: 64234ce5-dc46-4c8a-a316-61956b6b9abb
author: rothja
ms.author: jroth
ms.openlocfilehash: 286c2b199c83feca11a69e8d4d137ad5691f5362
ms.sourcegitcommit: c4d564435c008e2c92035efd2658172f20f07b2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88758799"
---
# <a name="provider-support-for-adox-ado"></a>Prise en charge de fournisseur pour ADOX (ADO)
Certaines fonctionnalités d’ADOX ne sont pas prises en charge, en fonction de votre fournisseur de données OLE DB. ADOX est entièrement pris en charge avec le [fournisseur de OLE DB pour Microsoft Jet](../appendixes/microsoft-ole-db-provider-for-microsoft-jet.md). Les fonctionnalités non prises en charge avec le [fournisseur microsoft OLE DB pour SQL Server](../appendixes/microsoft-ole-db-provider-for-sql-server.md), le [fournisseur Microsoft OLE DB pour ODBC](../appendixes/microsoft-ole-db-provider-for-odbc.md)ou le [fournisseur Microsoft OLE DB pour Oracle](../appendixes/microsoft-ole-db-provider-for-oracle.md) sont répertoriées dans les tableaux suivants. ADOX n’est pris en charge par aucun autre fournisseur Microsoft OLE DB.  
  
## <a name="microsoft-ole-db-provider-for-sql-server"></a>Fournisseur Microsoft OLE DB pour SQL Server  
  
|Objet ou collection|Restriction d’utilisation|  
|--------------------------|-----------------------|  
|**Tables** , collection|Les propriétés sont en lecture/écriture avant la création d’objets et en lecture seule lors du référencement d’un objet existant.|  
|**Views** , collection|Les **vues** ne sont pas prises en charge.|  
|**Procedures** , collection|Les méthodes **Append** et **Delete** ne sont pas prises en charge.|  
|Objet de **procédure**|La propriété **Command** n’est pas prise en charge.|  
|Collection **Keys**|Les méthodes **Append** et **Delete** ne sont pas prises en charge.|  
|Collection d' **utilisateurs**|**Les utilisateurs** ne sont pas pris en charge.|  
|Collection de **groupes**|Les **groupes** ne sont pas pris en charge.|  
  
## <a name="microsoft-ole-db-provider-for-odbc"></a>Fournisseur Microsoft OLE DB pour ODBC  
  
|Objet ou collection|Restriction d’utilisation|  
|--------------------------|-----------------------|  
|Objet **catalogue**|La méthode **Create** n’est pas prise en charge.|  
|**Tables** , collection|Les méthodes **Append** et **Delete** ne sont pas prises en charge. Les propriétés sont en lecture/écriture avant la création d’objets et en lecture seule lors du référencement d’un objet existant.|  
|**Procedures** , collection|Les méthodes **Append** et **Delete** ne sont pas prises en charge.|  
|Objet de **procédure**|La propriété **Command** n’est pas prise en charge.|  
|**Indexer** la collection|Les méthodes **Append** et **Delete** ne sont pas prises en charge.|  
|Collection **Keys**|Les méthodes **Append** et **Delete** ne sont pas prises en charge.|  
|Collection d' **utilisateurs**|**Les utilisateurs** ne sont pas pris en charge.|  
|Collection de **groupes**|Les **groupes** ne sont pas pris en charge.|  
  
## <a name="microsoft-ole-db-provider-for-oracle"></a>Fournisseur Microsoft OLE DB pour Oracle  
  
|Objet ou collection|Restriction d’utilisation|  
|--------------------------|-----------------------|  
|Objet **catalogue**|La méthode **Create** n’est pas prise en charge.|  
|**Tables** , collection|Les méthodes **Append** et **Delete** ne sont pas prises en charge. Les propriétés sont en lecture/écriture avant la création d’objets et en lecture seule lors du référencement d’un objet existant.|  
|**Views** , collection|Les méthodes **Append** et **Delete** ne sont pas prises en charge.|  
|**Afficher** l’objet|La propriété **Command** n’est pas prise en charge.|  
|Objet **procedures**|Les méthodes **Append** et **Delete** ne sont pas prises en charge.|  
|Objet de **procédure**|La propriété **Command** n’est pas prise en charge.|  
|**Indexer** la collection|Les méthodes **Append** et **Delete** ne sont pas prises en charge.|  
|Collection **Keys**|Les méthodes **Append** et **Delete** ne sont pas prises en charge.|  
|Collection d' **utilisateurs**|**Les utilisateurs** ne sont pas pris en charge.|  
|Collection de **groupes**|Les **groupes** ne sont pas pris en charge.|