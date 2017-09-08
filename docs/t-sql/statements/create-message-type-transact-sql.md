---
title: "CRÉER le TYPE DE MESSAGE (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 04/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_MESSAGE_TSQL
- MESSAGE_TSQL
- MESSAGE
- CREATE MESSAGE
- CREATE_MESSAGE_TYPE_TSQL
- MESSAGE TYPE
- MESSAGE_TYPE_TSQL
- CREATE MESSAGE TYPE
dev_langs:
- TSQL
helpviewer_keywords:
- XML [Service Broker]
- validation [Service Broker]
- message types [Service Broker], creating
- empty messages [SQL Server]
- binary [SQL Server], message types
- CREATE MESSAGE TYPE statement
ms.assetid: 98fe0fff-1a2e-4ca2-b37f-83a06fdf098e
caps.latest.revision: 41
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f8869a53cf18a58ba58b02e6faf8a42231e971e5
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="create-message-type-transact-sql"></a>CREATE MESSAGE TYPE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crée un nouveau type de message. Un type de message définit le nom d'un message et la validation effectuée par [!INCLUDE[ssSB](../../includes/sssb-md.md)] sur les messages portant ce nom. Les deux parties d'une conversation doivent définir les mêmes types de messages.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
CREATE MESSAGE TYPE message_type_name  
    [ AUTHORIZATION owner_name ]  
    [ VALIDATION = {  NONE  
                    | EMPTY   
                    | WELL_FORMED_XML  
                    | VALID_XML WITH SCHEMA COLLECTION schema_collection_name  
                   } ]  
[ ; ]  
```  
  
## <a name="arguments"></a>Arguments  
 *message_type_name*  
 Nom du type de message à créer. Un nouveau type de message est créé dans la base de données active et possédé par le principal spécifié dans la clause AUTHORIZATION. Les noms du serveur, de la base de données et du schéma ne peuvent pas être spécifiés. Le *message_type_name* peut contenir jusqu'à 128 caractères.  
  
 AUTORISATION *owner_name*  
 Définit le propriétaire du type de message sur l'utilisateur ou le rôle de base de données spécifié. Lorsque l’utilisateur actuel est **dbo** ou **sa**, *owner_name* peut être le nom de n’importe quel utilisateur ou rôle valide. Dans le cas contraire, *owner_name* doit être le nom de l’utilisateur actuel, le nom d’un utilisateur qui l’utilisateur actuel possède l’autorisation IMPERSONATE ou le nom d’un rôle auquel appartient l’utilisateur actuel. Lorsque cette clause est ignorée, le type de message appartient à l'utilisateur actuel.  
  
 VALIDATION  
 Spécifie comment [!INCLUDE[ssSB](../../includes/sssb-md.md)] valide le corps des messages de ce type. Lorsque cette clause n'est pas spécifiée, la validation par défaut est NONE.  
  
 Aucune  
 Spécifie qu'aucune validation n'est réalisée. Le corps du message peut contenir des données ou avoir la valeur NULL.  
  
 EMPTY  
 Spécifie que le corps du message doit avoir la valeur NULL.  
  
 WELL_FORMED_XML  
 Spécifie que le corps du message doit contenir du code XML correct.  
  
 VALID_XML WITH SCHEMA COLLECTION *schema_collection_name*  
 Spécifie que le corps du message doit contenir de code XML conforme à un schéma dans la collection de schémas spécifié le *schema_collection_name* doit être le nom d’une collection de schémas XML existante.  
  
## <a name="remarks"></a>Notes  
 [!INCLUDE[ssSB](../../includes/sssb-md.md)] valide les messages entrants. Lorsqu'un message contient un corps de message non conforme au type de validation spécifié, [!INCLUDE[ssSB](../../includes/sssb-md.md)] ignore le message non valide et retourne un message d'erreur au service émetteur du message.  
  
 Les deux parties d'une conversation doivent définir le même nom pour un type de message. Pour faciliter le dépannage, les deux parties d'une conversation spécifient généralement la même validation pour le type de message, bien que [!INCLUDE[ssSB](../../includes/sssb-md.md)] ne l'impose pas.  
  
 Il est possible qu'un type de message ne soit pas un objet temporaire. Les noms commençant par type de message  **#**  sont autorisées, mais sont des objets permanents.  
  
## <a name="permissions"></a>Permissions  
 L’autorisation de création d’un type de message par défaut, les membres de la **db_ddladmin** ou **db_owner** base de données fixe et le **sysadmin** rôle serveur fixe.  
  
 L’autorisation REFERENCES pour un type de message par défaut est le propriétaire du type de message, les membres du **db_owner** fixe du rôle de base de données et les membres de la **sysadmin** rôle serveur fixe.  
  
 Lorsque l'instruction CREATE MESSAGE TYPE spécifie une collection de schémas, l'utilisateur exécutant l'instruction doit disposer d'une autorisation REFERENCES sur la collection de schémas spécifiée.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-creating-a-message-type-containing-well-formed-xml"></a>A. Création d'un type de message contenant du code XML correct  
 L'exemple suivant crée un type de message contenant du code XML correct.  
  
```  
CREATE MESSAGE TYPE  
  [//Adventure-Works.com/Expenses/SubmitExpense]  
  VALIDATION = WELL_FORMED_XML ;     
```  
  
### <a name="b-creating-a-message-type-containing-typed-xml"></a>B. Création d'un type de message contenant du code XML typé  
 L'exemple suivant crée un type de message pour un rapport de frais encodé en XML. L'exemple crée une collection de schémas XML contenant le schéma d'un rapport de frais simple. L'exemple crée ensuite un type de message qui valide les messages par rapport au schéma.  
  
```  
CREATE XML SCHEMA COLLECTION ExpenseReportSchema AS  
N'<?xml version="1.0" encoding="UTF-16" ?>  
  <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
     targetNamespace="http://Adventure-Works.com/schemas/expenseReport"  
     xmlns:expense="http://Adventure-Works.com/schemas/expenseReport"  
     elementFormDefault="qualified"  
   >   
    <xsd:complexType name="expenseReportType">  
       <xsd:sequence>  
         <xsd:element name="EmployeeName" type="xsd:string"/>  
         <xsd:element name="EmployeeID" type="xsd:string"/>  
         <xsd:element name="ItemDetail"  
           type="expense:ItemDetailType" maxOccurs="unbounded"/>  
      </xsd:sequence>  
    </xsd:complexType>  
  
    <xsd:complexType name="ItemDetailType">  
      <xsd:sequence>  
        <xsd:element name="Date" type="xsd:date"/>  
        <xsd:element name="CostCenter" type="xsd:string"/>  
        <xsd:element name="Total" type="xsd:decimal"/>  
        <xsd:element name="Currency" type="xsd:string"/>  
        <xsd:element name="Description" type="xsd:string"/>  
      </xsd:sequence>  
    </xsd:complexType>  
  
    <xsd:element name="ExpenseReport" type="expense:expenseReportType"/>  
  
  </xsd:schema>' ;  
  
  CREATE MESSAGE TYPE  
    [//Adventure-Works.com/Expenses/SubmitExpense]  
    VALIDATION = VALID_XML WITH SCHEMA COLLECTION ExpenseReportSchema ;  
```  
  
### <a name="c-creating-a-message-type-for-an-empty-message"></a>C. Création d'un type de message pour un message vide  
 L'exemple suivant crée un type de message avec un encodage vide.  
  
```  
CREATE MESSAGE TYPE  
    [//Adventure-Works.com/Expenses/SubmitExpense]  
    VALIDATION = EMPTY ;  
```  
  
### <a name="d-creating-a-message-type-containing-binary-data"></a>D. Création d'un type de message contenant des données binaires  
 L'exemple suivant crée un type de message qui contient des données binaires. Étant donné que le message contient des données non XML, le type de message spécifie le type de validation `NONE`. Notez que dans ce cas, l'application qui reçoit un message de ce type doit vérifier que le message contient des données et que ces dernières sont du type attendu.  
  
```  
CREATE MESSAGE TYPE  
    [//Adventure-Works.com/Expenses/ReceiptImage]  
    VALIDATION = NONE ;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER MESSAGE TYPE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-message-type-transact-sql.md)   
 [SUPPRIMER le TYPE DE MESSAGE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-message-type-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

