---
title: sp_syscollector_update_collector_type (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_update_collector_type_TSQL
- sp_syscollector_update_collector_type
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syscollector_update_collector_type
- data collector [SQL Server], stored procedures
ms.assetid: 3c414dfd-d9ca-4320-81aa-949465b967bf
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9d3529d01966c7f9780183d663823d8f4033f47a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63001360"
---
# <a name="spsyscollectorupdatecollectortype-transact-sql"></a>sp_syscollector_update_collector_type (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Met à jour un type de collecteur pour un élément de collecte. Le nom et le GUID d'un type de collecteur étant fournis, met à jour la configuration du type de collecteur, y compris le package de collection et de téléchargement, le schéma de paramètres et le schéma du formateur de paramètres.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_syscollector_update_collector_type [ @collector_type_uid = ] 'collector_type_uid' OUTPUT  
          , [ @name = ] 'name'  
          , [ @parameter_schema = ] 'parameter_schema'  
          , [ @collection_package_id = ] collection_package_id  
          , [ @upload_package_id = ] upload_package_id  
```  
  
## <a name="arguments"></a>Arguments  
`[ @collector_type_uid = ] 'collector_type_uid'` Est le GUID pour le type de collecteur. *collector_type_uid* est **uniqueidentifier**, et si sa valeur est NULL, il sera automatiquement créée et retournée en tant que sortie.  
  
`[ @name = ] 'name'` Est le nom du type de collecteur. *nom* est **sysname** et doit être spécifié.  
  
`[ @parameter_schema = ] 'parameter_schema'` Est le schéma XML pour ce type de collecteur. *parameter_schema* est **xml** et peut être requis par certains types de collecteurs. S'il n'est pas requis, cet argument peut avoir la valeur NULL.  
  
`[ @collection_package_id = ] collection_package_id` Est un identificateur unique local qui pointe vers le [!INCLUDE[ssIS](../../includes/ssis-md.md)] package de collection utilisé par l’ensemble de la collection. *collection_package_id* est **uniqueidentifer** et est obligatoire. Pour obtenir la valeur de *collection_package_id*, interrogez la vue de système dbo.syscollector_collector_types dans la base de données msdb.  
  
`[ @upload_package_id = ] upload_package_id` Est un identificateur unique local qui pointe vers le [!INCLUDE[ssIS](../../includes/ssis-md.md)] télécharger le package utilisé par l’ensemble de la collection. *upload_package_id* est **uniqueidentifier** et est obligatoire. Pour obtenir la valeur de *upload_package_id*, interrogez la vue de système dbo.syscollector_collector_types dans la base de données msdb.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l’appartenance dans le **dc_admin** (avec autorisation EXECUTE) rôle fixe de base de données.  
  
## <a name="example"></a>Exemple  
 Cet exemple met à jour le type de collecteur Requête T-SQL générique. (Dans l'exemple, le schéma par défaut du type de collecteur Requête T-SQL générique est utilisé.)  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_update_collector_type  
@collector_type_uid = '302E93D1-3424-4BE7-AA8E-84813ECF2419',  
@name = 'Generic T-SQL Query Collector Type',  
@parameter_schema = '<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="DataCollectorType">  
  <xs:element name="TSQLQueryCollector">  
<xs:complexType>  
  <xs:sequence>  
<xs:element name="Query" minOccurs="1" maxOccurs="unbounded">  
  <xs:complexType>  
<xs:sequence>  
  <xs:element name="Value" type="xs:string" />  
  <xs:element name="OutputTable" type="xs:string" />  
</xs:sequence>  
  </xs:complexType>  
</xs:element>  
<xs:element name="Databases" minOccurs="0" maxOccurs="1">  
  <xs:complexType>  
<xs:sequence>  
  <xs:element name="Database" minOccurs="0" maxOccurs="unbounded" type="xs:string" />  
</xs:sequence>  
<xs:attribute name="UseSystemDatabases" type="xs:boolean" use="optional" />  
<xs:attribute name="UseUserDatabases" type="xs:boolean" use="optional" />  
  </xs:complexType>  
</xs:element>  
  </xs:sequence>  
</xs:complexType>  
  </xs:element>  
</xs:schema>',  
@collection_package_id = '292B1476-0F46-4490-A9B7-6DB724DE3C0B',  
@upload_package_id = '6EB73801-39CF-489C-B682-497350C939F0';  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Collecte de données](../../relational-databases/data-collection/data-collection.md)  
  
  
