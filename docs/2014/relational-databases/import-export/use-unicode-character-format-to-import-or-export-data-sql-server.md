---
title: Utiliser le format caractère Unicode pour importer ou exporter des données (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- data formats [SQL Server], Unicode character
- Unicode [SQL Server], bulk importing and exporting
ms.assetid: 74342a11-c1c0-4746-b482-7f3537744a70
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 85df40b07542e1af144796d4e8b5f9fb33cdc7c9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63065758"
---
# <a name="use-unicode-character-format-to-import-or-export-data-sql-server"></a>Utiliser le format caractère Unicode pour importer ou exporter des données (SQL Server)
  Le format caractère Unicode est recommandé pour le transfert en bloc de données entre plusieurs instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'aide d'un fichier de données qui contient des caractères étendus ou DBCS. Le format de données caractère Unicode permet d'exporter des données depuis un serveur à l'aide d'une page de codes différente de celle utilisée par le client qui effectue l'opération. Dans ces cas, l'utilisation du format caractère Unicode présente les avantages suivants :  
  
-   Si les données sources et de destination sont de types de données Unicode, l'utilisation du format caractère Unicode conserve toutes les données caractère.  
  
-   Si les données sources et de destination ne sont pas de types de données Unicode, l'utilisation du format caractère Unicode réduit au minimum la perte de caractères étendus dans les données sources qui ne peuvent pas être représentées sur la destination.  
  
 Les fichiers de données de format caractère Unicode respectent les conventions pour les fichiers Unicode. Les deux premiers octets du fichier sont des nombres hexadécimaux (0xFFFE). Ces octets sont utilisés comme indicateurs de l'ordre des octets, précisant si l'octet de poids fort est enregistré en premier ou en dernier dans le fichier.  
  
> [!IMPORTANT]  
>  Pour qu'un fichier de format fonctionne avec un fichier de données de caractères Unicode, tous les champs d'entrée doivent être des chaînes de texte Unicode (autrement dit, des chaînes Unicode de taille fixe ou terminées par un caractère).  
  
 Les données `sql_variant` stockées dans un fichier de données de format caractère Unicode fonctionnent comme dans un fichier de données de format caractère, à la différence que les données sont stockées en tant que données `nchar` et non pas `char`. Pour plus d’informations sur le format caractère, consultez [Prise en charge d’Unicode et du classement](../collations/collation-and-unicode-support.md).  
  
 Pour utiliser un indicateur de fin de champ ou de ligne autre que l’indicateur par défaut du format caractère Unicode, consultez [Spécifier des indicateurs de fin de champ et de fin de ligne &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md).  
  
## <a name="command-options-for-unicode-character-format"></a>Options de commande du format caractère Unicode  
 Vous pouvez importer des données au format caractère Unicode dans une table à l’aide de la commande **bcp**, BULK INSERT ou INSERT... SELECT \* FROM OPENROWSET(BULK...). Si vous utilisez une commande **bcp** ou une instruction BULK INSERT, vous pouvez spécifier le format de données dans la ligne de commande. Pour une instruction INSERT ... SELECT * FROM OPENROWSET(BULK...), vous devez spécifier le format de données dans un fichier de format.  
  
 Le format caractère Unicode est pris en charge par les options de ligne de commande suivantes :  
  
|Command|Option|Description|  
|-------------|------------|-----------------|  
|**bcp**|**-w**|Utilise le format caractère Unicode.|  
|BULK INSERT|DATAFILETYPE **='** widechar **'**|Utilise le format caractère Unicode lors de l'importation de données en bloc.|  
  
 Pour plus d’informations, consultez [Utilitaire bcp](../../tools/bcp-utility.md), [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) ou [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).  
  
> [!NOTE]  
>  Vous pouvez également spécifier le formatage par champ dans un fichier de format. Pour plus d’informations, consultez [Fichiers de format pour l’importation ou l’exportation de données &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).  
  
## <a name="examples"></a>Exemples  
 Les exemples suivants montrent comment exporter en bloc des données de caractères Unicode à l’aide de la commande **bcp** et importer en bloc les mêmes données à l’aide de l’instruction BULK INSERT.  
  
### <a name="sample-table"></a>Exemple de table  
 Une table nommée `myTestUniCharData` doit être créée dans l'exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sous le schéma `dbo` . Avant de commencer, vous devez créer cette base de données. Pour créer cette table, dans l'éditeur de requêtes [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] , exécutez le code suivant :  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE myTestUniCharData (  
   Col1 smallint,  
   Col2 nvarchar(50),  
   Col3 nvarchar(50)  
   );   
```  
  
 Pour remplir cette table et afficher le contenu résultant, exécutez les instructions suivantes :  
  
```  
INSERT INTO myTestUniCharData(Col1,Col2,Col3)  
   VALUES(1,'DataField2','DataField3')   
        ,(2,'DataField2','DataField3');  
GO  
SELECT Col1,Col2,Col3 FROM myTestUniCharData;  
  
```  
  
### <a name="using-bcp-to-bulk-export-unicode-character-data"></a>Utilisation de la commande bcp pour exporter en bloc des données caractère Unicode  
 Pour exporter des données de la table vers le fichier de données, utilisez **bcp** avec l’option **out** et les qualificateurs suivants :  
  
|Qualificateurs|Description|  
|----------------|-----------------|  
|**-w**|Spécifie le format caractère Unicode.|  
|**-t** `,`|Virgule (`,`) servant d'indicateur de fin de champ.<br /><br /> Remarque : La marque de fin de champ par défaut est le caractère Unicode (\t). Pour plus d’informations, consultez [Spécifier des indicateurs de fin de champ et de fin de ligne &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md).|  
|**-T**|Spécifie que l'utilitaire **bcp** se connecte à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec une connexion approuvée qui utilise la sécurité intégrée. Si **-T** n’est pas spécifié, vous devez indiquer **-U** et **-P** pour vous connecter.|  
  
 L'exemple suivant exporte en bloc des données au format de caractères Unicode à partir de la table `myTestUniCharData` dans un nouveau fichier de données nommé `myTestUniCharData-w.Dat` qui utilise la virgule (`,`) comme marque de fin de champ. À l'invite de commandes [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, entrez :  
  
```  
bcp AdventureWorks2012..myTestUniCharData out C:\myTestUniCharData-w.Dat -w -t, -T  
  
```  
  
### <a name="using-bulk-insert-to-bulk-import-unicode-character-data"></a>Utilisation de l'instruction BULK INSERT pour importer en bloc des données caractère Unicode  
 Dans l'exemple ci-dessous, l'instruction `BULK INSERT` est employée pour importer les données du fichier de données `myTestUniCharData-w.Dat` dans la table `myTestUniCharData`. La marque de fin de champ autre que celle par défaut (`,`) doit être déclarée dans l'instruction. Dans l'Éditeur de requête [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] , exécutez :  
  
```  
USE AdventureWorks2012;  
GO  
BULK INSERT myTestUniCharData   
   FROM 'C:\myTestUniCharData-w.Dat'   
   WITH (  
      DATAFILETYPE='widechar',  
      FIELDTERMINATOR=','  
   );   
GO  
SELECT Col1,Col2,Col3 FROM myTestUniCharData;  
GO  
  
```  
  
##  <a name="RelatedTasks"></a> Tâches associées  
 **Pour utiliser des formats de données pour l'importation ou l'exportation en bloc**  
  
-   [Importer des données au format natif et caractère à partir de versions antérieures de SQL Server](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [Utiliser le format caractère pour importer ou exporter des données &#40;SQL Server&#41;](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Utiliser le format natif pour importer ou exporter des données &#40;SQL Server&#41;](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Utiliser le format natif Unicode pour importer ou exporter des données &#40;SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
## <a name="see-also"></a>Voir aussi  
 [bcp Utility](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)   
 [Types de données &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)   
 [Prise en charge d’Unicode et du classement](../collations/collation-and-unicode-support.md)  
  
  
