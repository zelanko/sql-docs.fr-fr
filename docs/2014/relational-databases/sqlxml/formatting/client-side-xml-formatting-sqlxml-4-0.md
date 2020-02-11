---
title: Mise en forme XML côté client (SQLXML 4,0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- FOR XML clause, formatting
- middle tier XML formatting [SQLXML]
- client-side XML formatting
- client-side-xml attribute
ms.assetid: 9630a21d-a93b-4d3b-8a25-c4b32399f993
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 89f1327a7672d7de5b480bf3b8757b0c85ff138f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66012317"
---
# <a name="client-side-xml-formatting-sqlxml-40"></a>Mise en forme XML côté client (SQLXML 4.0)
  Cette rubrique fournit des informations sur la mise en forme XML côté client. La mise en forme côté client fait référence à la mise en forme du code XML dans la couche intermédiaire.  
  
> [!NOTE]  
>  Cette rubrique fournit des informations supplémentaires sur l'utilisation de la clause FOR XML côté client ; elle suppose que la clause FOR XML vous est déjà familière. Pour plus d’informations sur FOR XML, consultez [construction de XML à l’aide de for XML](../../xml/for-xml-sql-server.md).  
  
 **Important** Pour utiliser la fonctionnalité FOR XML côté client avec le nouveau `xml` type de données, les clients doivent toujours [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utiliser le fournisseur de données Native Client (SQLNCLI11) au lieu du fournisseur SQLOLEDB. SQLNCLI11 est la version la plus récente du fournisseur SQL Server et prend complètement en charge les types de données apparus dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Avec l'utilisation de FOR XML côté client et du fournisseur SQLOLEDB, les types de données sont traités en tant que chaînes `xml`.  
  
## <a name="formatting-xml-documents-on-the-client-side"></a>Mise en forme de documents XML côté client  
 Lorsqu'une application cliente exécute la requête suivante :  
  
```  
SELECT FirstName, LastName  
FROM   Person.Contact  
FOR XML RAW  
```  
  
 ...seule cette partie de la requête est envoyée au serveur :  
  
```  
SELECT FirstName, LastName  
FROM   Person.Contact  
```  
  
 Le serveur exécute la requête et retourne un ensemble de lignes (qui contient FirstName et LastNamecolumns) au client. La couche intermédiaire applique ensuite la transformation FOR XML à l'ensemble de lignes et retourne la mise en forme XML au client.  
  
 De la même façon, lorsque vous exécutez une requête XPath, le serveur retourne l'ensemble de lignes au client et la transformation FOR XML EXPLICIT est appliquée à l'ensemble de lignes sur le client, ce qui génère la mise en forme XML souhaitée.  
  
 Le tableau suivant montre les modes que vous pouvez spécifier avec FOR XML côté client.  
  
|Mode FOR XML côté client|Commentaire|  
|-------------------------------|-------------|  
|RAW|Produit des résultats identiques lors de la spécification de FOR XML côté client ou côté serveur.|  
|NESTED|Est semblable au mode FOR XML AUTO côté serveur.|  
|EXPLICIT|Est semblable au mode FOR XML EXPLICIT côté serveur.|  
  
> [!NOTE]  
>  Si vous spécifiez le mode AUTO et si vous demandez une mise en forme XML côté client, la requête entière est envoyée au serveur ; en d'autres termes, la mise en forme XML s'effectue sur le serveur. Cela répond à une question de commodité. Toutefois, notez que le mode NESTED retourne les noms de tables de base en tant que noms d'éléments dans le document XML généré. Certaines des applications que vous écrivez peuvent nécessiter des noms de tables de base. Par exemple, vous pouvez exécuter une procédure stockée et charger les données résultantes dans un dataset (dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)].NET Framework), puis générer ultérieurement un DiffGram pour mettre à jour les données dans les tables. Dans ce cas, vous avez besoin des informations sur les tables de base et vous devez utiliser le mode NESTED.  
  
## <a name="benefits-of-client-side-xml-formatting"></a>Avantages de la mise en forme XML côté client  
 Vous trouverez ci-après la description de certains avantages liés à la mise en forme XML sur le client.  
  
### <a name="if-you-have-stored-procedures-on-the-server-that-return-a-single-rowset-you-can-request-client-side-for-xml-transformation-to-generate-an-xml"></a>Si vous avez des procédures stockées sur le serveur qui retournent un ensemble de lignes unique, vous pouvez demander une transformation FOR XML côté client pour générer du code XML.  
 Prenons l'exemple de la procédure stockée ci-dessous. Cette procédure retourne les noms et prénoms des employés à partir de la table Person.Contact de la base de données AdventureWorks :  
  
```  
IF EXISTS (SELECT name FROM sysobjects  
   WHERE name = 'GetContacts' AND type = 'P')  
   DROP PROCEDURE GetContacts  
GO  
CREATE PROCEDURE GetContacts  
AS  
    SELECT   FirstName, LastName  
    FROM     Person.Contact  
```  
  
 L'exemple de modèle XML suivant exécute la procédure stockée. La clause FOR XML est spécifiée après le nom de la procédure stockée.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="1">  
    EXEC GetContacts FOR XML NESTED  
  </sql:query>  
</ROOT>  
```  
  
 Étant donné que l’attribut **Client-Side-XML** a la valeur 1 (true) dans le modèle, la procédure stockée est exécutée sur le serveur et l’ensemble de lignes à deux colonnes retourné par le serveur est transformé en XML sur la couche intermédiaire et retourné au client. (Seul un résultat partiel est montré ici.)  
  
```  
 <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact FirstName="Gustavo" LastName="Achong" />   
  <Person.Contact FirstName="Catherine" LastName="Abel" />  
</ROOT>  
```  
  
> [!NOTE]  
>  Lorsque vous utilisez le fournisseur SQLXMLOLEDB ou les classes managées SQLXML, vous pouvez utiliser la propriété `ClientSideXml` pour demander une mise en forme XML côté client.  
  
### <a name="the-workload-is-more-balanced"></a>La charge de travail est plus équilibrée.  
 Dans la mesure où le client effectue la mise en forme XML, la charge de travail est équilibrée entre le serveur et le client, ce qui permet au serveur d'exécuter d'autres tâches.  
  
## <a name="supporting-client-side-xml-formatting"></a>Prise en charge de la mise en forme XML côté client  
 Pour permettre la prise en charge des fonctionnalités de mise en forme XML côté client, SQLXML offre les éléments suivants :  
  
-   fournisseur SQLXMLOLEDB  
  
-   classes managées SQLXML  
  
-   prise en charge améliorée du modèle XML.  
  
-   SqlXmlCommand. ClientSideXml, propriété  
  
     Vous pouvez spécifier la mise en forme côté client en définissant cette propriété des classes managées SQLXML à true.  
  
## <a name="enhanced-xml-template-support"></a>Prise en charge améliorée du modèle XML.  
 À partir [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]de, le modèle XML [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans a été amélioré avec l’ajout de l’attribut **XML côté client** . Si cet attribut a la valeur true, le code XML est mis en forme sur le client. Notez que cet attribut de modèle est identique dans les fonctionnalités de la propriété ClientSideXML spécifique au fournisseur SQLXMLOLEDB.  
  
> [!NOTE]  
>  Si vous exécutez un modèle XML dans une application ADO qui utilise le fournisseur SQLXMLOLEDB et que vous spécifiez à la fois l’attribut **Client-Side-XML** dans le modèle et la propriété ClientSideXML du fournisseur, la valeur spécifiée dans le modèle est prioritaire.  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture de la mise en forme XML côté client et côté serveur &#40;SQLXML 4,0&#41;](server-side-xml-formatting-sqlxml-4-0.md)   
 [FOR XML &#40;SQL Server&#41;](../../xml/for-xml-sql-server.md)   
 [Considérations relatives à la sécurité XML &#40;SQLXML 4,0&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/security/for-xml-security-considerations-sqlxml-4-0.md)   
 [Prise en charge des types de données XML dans SQLXML 4,0](../xml-data-type-support-in-sqlxml-4-0.md)   
 [Classes managées SQLXML](../../sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-4-0-net-framework-support-managed-classes.md)   
 [Mise en forme XML côté client et côté serveur &#40;SQLXML 4,0&#41;](client-side-vs-server-side-xml-formatting-sqlxml-4-0.md)   
 [Objet SqlXmlCommand &#40;les classes managées SQLXML&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-managed-classes-sqlxmlcommand-object.md)   
 [Données XML &#40;SQL Server&#41;](../../xml/xml-data-sql-server.md)  
  
  
