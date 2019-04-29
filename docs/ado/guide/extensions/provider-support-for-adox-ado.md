---
title: Prise en charge de fournisseur pour ADOX (ADO) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e6f346779d3a4c8cb43e2b30347ebf6b198d9015
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63126870"
---
# <a name="provider-support-for-adox-ado"></a>Prise en charge de fournisseur pour ADOX (ADO)
Certaines fonctionnalités d’ADOX ne sont pas pris en charge, en fonction de votre fournisseur de données OLE DB. ADOX est entièrement pris en charge avec le [fournisseur OLE DB pour Microsoft Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md). Les fonctionnalités non prises en charge avec le [fournisseur Microsoft OLE DB pour SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md), le [fournisseur Microsoft OLE DB pour ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md), ou le [fournisseur Microsoft OLE DB pour Oracle](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-oracle.md) sont répertoriées dans les tableaux suivants. ADOX n’est pas pris en charge par tous les autres fournisseurs OLE DB de Microsoft.  
  
## <a name="microsoft-ole-db-provider-for-sql-server"></a>Fournisseur Microsoft OLE DB pour SQL Server  
  
|Objet ou une Collection|Restriction d’utilisation|  
|--------------------------|-----------------------|  
|**Tables** collection|Propriétés sont en lecture/écriture avant la création d’objets et en lecture seule lors du référencement d’un objet existant.|  
|**Vues** collection|**Vues** n’est pas pris en charge.|  
|**Procédures** collection|Le **Append** et **supprimer** méthodes ne sont pas prises en charge.|  
|**Procédure** objet|Le **commande** propriété n’est pas prise en charge.|  
|**Clés** collection|Le **Append** et **supprimer** méthodes ne sont pas prises en charge.|  
|**Les utilisateurs** collection|**Les utilisateurs** n’est pas pris en charge.|  
|**Groupes** collection|**Groupes** n’est pas pris en charge.|  
  
## <a name="microsoft-ole-db-provider-for-odbc"></a>Fournisseur Microsoft OLE DB pour ODBC  
  
|Objet ou une Collection|Restriction d’utilisation|  
|--------------------------|-----------------------|  
|**Catalogue** objet|Le **créer** méthode n’est pas prise en charge.|  
|**Tables** collection|Le **Append** et **supprimer** méthodes ne sont pas prises en charge. Propriétés sont en lecture/écriture avant la création d’objets et en lecture seule lors du référencement d’un objet existant.|  
|**Procédures** collection|Le **Append** et **supprimer** méthodes ne sont pas prises en charge.|  
|**Procédure** objet|Le **commande** propriété n’est pas prise en charge.|  
|**Index** collection|Le **Append** et **supprimer** méthodes ne sont pas prises en charge.|  
|**Clés** collection|Le **Append** et **supprimer** méthodes ne sont pas prises en charge.|  
|**Les utilisateurs** collection|**Les utilisateurs** n’est pas pris en charge.|  
|**Groupes** collection|**Groupes** n’est pas pris en charge.|  
  
## <a name="microsoft-ole-db-provider-for-oracle"></a>Fournisseur Microsoft OLE DB pour Oracle  
  
|Objet ou une Collection|Restriction d’utilisation|  
|--------------------------|-----------------------|  
|**Catalogue** objet|Le **créer** méthode n’est pas prise en charge.|  
|**Tables** collection|Le **Append** et **supprimer** méthodes ne sont pas prises en charge. Propriétés sont en lecture/écriture avant la création d’objets et en lecture seule lors du référencement d’un objet existant.|  
|**Vues** collection|Le **Append** et **supprimer** méthodes ne sont pas prises en charge.|  
|**Vue** objet|Le **commande** propriété n’est pas prise en charge.|  
|**Procédures** objet|Le **Append** et **supprimer** méthodes ne sont pas prises en charge.|  
|**Procédure** objet|Le **commande** propriété n’est pas prise en charge.|  
|**Index** collection|Le **Append** et **supprimer** méthodes ne sont pas prises en charge.|  
|**Clés** collection|Le **Append** et **supprimer** méthodes ne sont pas prises en charge.|  
|**Les utilisateurs** collection|**Les utilisateurs** n’est pas pris en charge.|  
|**Groupes** collection|**Groupes** n’est pas pris en charge.|
