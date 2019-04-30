---
title: Conseiller de compilation native | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
f1_keywords:
- sql12.swb.nativecompilationwizard.f1
- swb.nativecompilationwizard.f1
ms.assetid: d3898a47-2985-4a08-bc70-fd8331a01b7b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5174b5c859fa76ceeccdb99b7a46f510fd62d923
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63072752"
---
# <a name="native-compilation-advisor"></a>Conseiller de compilation native
  L'outil de génération de rapports sur les performances des transactions (voir [Déterminer si un tableau ou une procédure stockée doit être déplacée vers l'OLTP en mémoire](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)) vous indique quelles procédures stockées interprétées dans votre base de données tireront parti de l'utilisation de la compilation native. Après avoir identifié une procédure stockée que vous souhaitez déplacer pour utiliser la compilation native, vous pouvez utiliser le conseiller de compilation native pour vous aider à migrer la procédure stockée interprétée vers la compilation native. Pour plus d'informations sur les procédures stockées compilées en mode natif, consultez [Natively Compiled Stored Procedures](natively-compiled-stored-procedures.md).  
  
 Pour démarrer, connectez-vous à l'instance qui contient la procédure stockée interprétée. Vous pouvez vous connecter à l'instance [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]ou [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] . Toutefois, si vous souhaitez effectuer une opération de migration avec le conseiller, vous devez vous connecter à une instance [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] sur laquelle la fonctionnalité OLTP en mémoire est activée. Pour plus d'informations sur les spécifications applicables à la fonctionnalité OLTP en mémoire, consultez [Requirements for Using Memory-Optimized Tables](memory-optimized-tables.md).  
  
 Pour plus d’informations sur les méthodologies de migration, consultez [OLTP en mémoire - Modèles de charge de travail courants et considérations relatives à la migration](https://msdn.microsoft.com/library/dn673538.aspx).  
  
## <a name="walkthrough-using-the-native-compilation-advisor"></a>Procédure pas à pas d'utilisation du Conseiller de compilation native  
 Dans l' **Explorateur d'objets**, cliquez avec le bouton droit sur la procédure stockée à convertir, puis sélectionnez **Conseiller de compilation native**. Ce faisant, vous affichez la page d'accueil du **Conseiller compilation native de procédure stockée**. Cliquez sur **Suivant** pour continuer.  
  
### <a name="stored-procedure-validation"></a>Validation de la procédure stockée  
 Cette page signale si la procédure stockée utilise des éléments qui ne sont pas compatibles avec la compilation native. Vous pouvez cliquer sur **Suivant** pour afficher les détails. Si certains éléments ne sont pas compatibles avec la compilation native, vous pouvez cliquer sur **Suivant** pour afficher les détails.  
  
### <a name="stored-procedure-validation-result"></a>Résultats de la validation de la procédure stockée  
 Si certains éléments ne sont pas compatibles avec la compilation native, la page **Résultat de la validation de la procédure stockée** affiche les détails. Vous pouvez générer un rapport (cliquez sur **Générer le rapport**), quitter le **Conseiller de compilation native**et mettre à jour votre code afin qu’il soit compatible avec la compilation native.  
  
## <a name="code-sample"></a>Exemple de code  
 L'exemple suivant illustre une procédure stockée interprétée et la procédure stockée équivalente pour la compilation native. L'exemple suppose la présence d'un répertoire appelé c:\data.  
  
```sql  
CREATE DATABASE Demo  
ON  
PRIMARY(NAME = [Demo_data],  
FILENAME = 'C:\DATA\Demo_data.mdf', size=500MB)  
, FILEGROUP [Demo_fg] CONTAINS MEMORY_OPTIMIZED_DATA(  
NAME = [Demo_dir],  
FILENAME = 'C:\DATA\Demo_dir')  
LOG ON (name = [Demo_log], Filename='C:\DATA\Demo_log.ldf', size=500MB)  
COLLATE Latin1_General_100_BIN2;  
GO  
USE Demo;  
GO  
  
CREATE TABLE [dbo].[SalesOrders]  
(  
     [order_id] [int] NOT NULL,  
     [order_date] [datetime] NOT NULL,  
     [order_status] [tinyint] NOT NULL  
  
CONSTRAINT [PK_SalesOrders] PRIMARY KEY NONCLUSTERED HASH   
(  
     [order_id]  
)WITH ( BUCKET_COUNT = 2097152)  
)WITH ( MEMORY_OPTIMIZED = ON )  
  
go  
  
CREATE PROCEDURE [dbo].[InsertOrder] @id INT, @date DATETIME2, @status TINYINT  
AS   
BEGIN   
  
  INSERT dbo.SalesOrders VALUES (@id, @date, @status)  
  
END  
  
go  
  
CREATE PROCEDURE [dbo].[InsertOrderXTP] @id INT, @date DATETIME2, @status TINYINT  
  WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS   
BEGIN ATOMIC WITH   
(    TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
     LANGUAGE = N'us_english')  
  
  INSERT dbo.SalesOrders VALUES (@id, @date, @status)  
  
END  
go  
  
select * from SalesOrders  
go  
exec dbo.InsertOrder @id= 10, @date = '1956-01-01 12:00:00', @status = 1 ;  
exec dbo.InsertOrderXTP @id= 11, @date = '1956-01-01 12:01:00', @status = 2 ;  
select * from SalesOrders  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Migration vers OLTP en mémoire](migrating-to-in-memory-oltp.md)  
  
  
