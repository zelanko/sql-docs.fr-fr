---
title: Introduction au chargement en masse XML (SQLXML)
description: En savoir plus sur l’utilitaire de chargement en masse XML, un objet COM autonome dans SQLXML 4,0 qui vous permet de charger des données XML semi-structurées dans des tables Microsoft SQL Server.
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- nontransacted XML Bulk Load operations
- XML Bulk Load [SQLXML], about XML Bulk Load
- bulk load [SQLXML], about bulk load
- transacted XML Bulk Load operations
- streaming XML data
ms.assetid: 38bd3cbd-65ef-4c23-9ef3-e70ecf6bb88a
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1fe57f7f0376e6c9691808c224d33c1796d65812
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85762821"
---
# <a name="introduction-to-xml-bulk-load-sqlxml-40"></a>Présentation du chargement en masse XML (SQLXML 4.0)
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]
  Le chargement en masse XML est un objet COM autonome qui vous permet de charger des données XML semi-structurées dans des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tables Microsoft.  
  
 Vous pouvez insérer les données XML dans une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à l'aide d'une instruction INSERT et de la fonction OPENXML ; toutefois, l'utilitaire de chargement en masse fournit de meilleures performances lorsque vous avez besoin d'insérer des quantités importantes de données XML.  
  
 La méthode Execute du modèle objet de chargement en masse XML accepte deux paramètres :  
  
-   Un schéma XSD (XML Schema Definition)) ou XDR (XML-Data Reduced) annoté. L'utilitaire de chargement en masse XML interprète ce schéma de mappage et les annotations spécifiées dans le schéma pour identifier les tables SQL Server dans lesquelles les données XML doivent être insérées.  
  
-   Un document ou un fragment de document XML (un fragment de document est un document sans élément de niveau supérieur unique). Un nom de fichier ou un flux pouvant être lu par le chargement en masse XML peut être spécifié.  
  
 Le chargement en masse XML interprète le schéma de mappage et identifie le ou les tables dans lesquelles les données XML doivent être insérées.  
  
 Cette rubrique suppose que vous connaissez bien les fonctionnalités [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] suivantes :  
  
-   Schémas XSD et XDR annotés. Pour plus d’informations sur les schémas XSD annotés, consultez [Présentation des schémas XSD Annotés &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md). Pour plus d’informations sur les schémas XDR annotés, consultez [schémas XDR Annotés &#40;dépréciés dans SQLXML 4,0&#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).  
  
-   Mécanismes d'insertion en bloc [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], tels que l'instruction [!INCLUDE[tsql](../../../includes/tsql-md.md)] BULK INSERT et l'utilitaire bcp. Pour plus d’informations, consultez [BULK INSERT &#40;Transact-SQL&#41;](../../../t-sql/statements/bulk-insert-transact-sql.md) et [utilitaire bcp](../../../tools/bcp-utility.md).  
  
## <a name="streaming-of-xml-data"></a>Diffusion en continu de données XML  
 Le document XML source pouvant être volumineux, le document n'est pas lu intégralement en mémoire au cours du traitement de chargement en masse. Au lieu de cela, le chargement en masse XML interprète les données XML en tant que flux et lit ce flux. À mesure que l'utilitaire lit les données, il identifie la ou les tables de base de données, génère le ou les enregistrements appropriés à partir de la source de données XML, puis envoie le ou les enregistrements à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à des fins d'insertion.  
  
 Par exemple, le document XML source suivant se compose d' **\<Customer>** éléments et d' **\<Order>** éléments enfants :  
  
```  
<Customer ...>  
    <Order.../>  
    <Order .../>  
     ...  
</Customer>  
...  
```  
  
 À mesure que le chargement en masse XML lit l' **\<Customer>** élément, il génère un enregistrement pour le CustomerTable. Lorsqu’il lit la **\</Customer>** balise de fin, le chargement en masse XML insère cet enregistrement dans la table de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . De la même façon, lors de la lecture de l' **\<Order>** élément, le chargement en masse XML génère un enregistrement pour le Ordertable, puis insère cet enregistrement dans la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] table lors de la lecture de la **\</Order>** balise de fin.  
  
## <a name="transacted-and-nontransacted-xml-bulk-load-operations"></a>Opérations de chargement en masse XML transactionnelles et non transactionnelles  
 Le chargement en masse XML peut fonctionner en mode transactionnel ou non transactionnel. Les performances sont généralement optimales si vous effectuez un chargement en masse en mode non-. autrement dit, la propriété transaction est définie sur FALSe et l’une ou l’autre des conditions suivantes est vraie :  
  
-   Les tables dans lesquelles les données sont chargées en masse sont vides et ne comprennent pas d'index.  
  
-   Les tables ont des données et des index uniques.  
  
 L'approche non transactionnelle ne garantit pas de restauration en cas de problème dans le processus de chargement en masse (bien que des restaurations partielles puissent se produire). Le chargement en masse non transactionnel est approprié lorsque la base de données est vide. Par conséquent, en cas de problème, vous pouvez nettoyer la base de données et redémarrer le chargement en masse XML.  
  
> [!NOTE]  
>  En mode non transactionnel, le chargement en masse XML utilise une transaction interne par défaut et la valide. Lorsque la propriété transaction a la valeur TRUE, le chargement en masse XML n’appelle pas la validation sur cette transaction.  
  
 Si la propriété transaction est définie sur TRUE, le chargement en masse XML crée des fichiers temporaires, un pour chaque table identifiée dans le schéma de mappage. Le chargement en masse XML commence par stocker les enregistrements du document XML source dans ces fichiers temporaires. Ensuite, une instruction [!INCLUDE[tsql](../../../includes/tsql-md.md)] BULK INSERT récupère ces enregistrements des fichiers et les stocke dans les tables correspondantes. Vous pouvez spécifier l’emplacement de ces fichiers temporaires à l’aide de la propriété TempFilePath. Vous devez vous assurer que le compte [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilisé avec le chargement en masse XML a accès à ce chemin d'accès. Si la propriété TempFilePath n’est pas spécifiée, le chemin d’accès au fichier par défaut qui est spécifié dans la variable d’environnement TEMP est utilisé pour créer les fichiers temporaires.  
  
 Si la propriété transaction est définie sur FALSe (paramètre par défaut), le chargement en masse XML utilise l’interface OLE DB IRowsetFastLoad pour charger en masse les données.  
  
 Si la propriété ConnectionString définit la chaîne de connexion et que la propriété transaction a la valeur TRUE, le chargement en masse XML opère dans son propre contexte de transaction. (Par exemple, le chargement en masse XML démarre sa propre transaction, puis effectue une validation ou une restauration comme il convient.)  
  
 Si la propriété ConnectionCommand définit la connexion avec un objet de connexion existant et que la propriété transaction a la valeur TRUE, le chargement en masse XML n’émet pas d’instruction COMMIT ou ROLLBACK en cas de succès ou d’échec, respectivement. En cas d'erreur, le chargement en masse XML retourne le message d'erreur approprié. La décision d'émettre une instruction COMMIT ou ROLLBACK appartient au client qui a initialisé le chargement en masse. L’objet de connexion utilisé pour le chargement en masse XML doit être de type ICommand ou d’un objet de commande ADO.  
  
 Dans SQLXML 4,0, un ConnectionObject ne peut pas être utilisé avec la propriété transaction définie sur FALSe. Le mode non-Transact-1 n’est pas pris en charge avec un ConnectionObject, car il est impossible d’ouvrir plusieurs interfaces IRowsetFastLoad sur une session passée.  
  
  
