---
title: Utiliser le format caractère pour importer ou exporter des données (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- data formats [SQL Server], character
- character formats [SQL Server]
ms.assetid: d925e66a-1a73-43cd-bc06-1cbdf8174a4d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ab658be26dc8ccbdd4e760d0b1bc835ace3b2c38
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66011671"
---
# <a name="use-character-format-to-import-or-export-data-sql-server"></a>Utiliser le format caractère pour importer ou exporter des données (SQL Server)
  Le format caractère est recommandé pour l'exportation en bloc de données dans un fichier texte qui doit être utilisé dans un autre programme, ou pour l'importation en bloc de données à partir d'un fichier texte généré par un autre programme.  
  
> [!NOTE]  
>  Lors du transfert en bloc de données entre des instances de [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , si le fichier de données contient des données caractères Unicode mais aucun caractère étendu ni jeu de caractères codés sur deux octets (DBCS), utilisez le format de caractères Unicode. Pour plus d’informations, consultez [Utiliser le format caractère Unicode pour importer ou exporter des données &#40;SQL Server&#41;](use-unicode-character-format-to-import-or-export-data-sql-server.md).  
  
 Le format caractère utilise le format de données de caractères pour toutes les colonnes. L'enregistrement d'informations au format caractère est utile lorsque les données sont exploitées par un autre programme, par exemple un tableur, ou lorsque les données doivent être copiées dans une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d'une base de données issue d'un autre éditeur comme Oracle.  
  
## <a name="considerations-for-using-character-format"></a>Considérations relatives à l'utilisation du format caractère  
 Lors de l'utilisation du format caractère, tenez compte des points suivants :  
  
-   Par défaut, l’utilitaire **bcp** sépare les champs de données de caractères par le caractère de tabulation et termine les enregistrements par un caractère de nouvelle ligne. Pour plus d’informations sur la spécification des terminateurs de remplacement, consultez [Spécifier des indicateurs de fin de champ et de fin de ligne &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md).  
  
-   Par défaut, avant l'exportation ou l'importation en bloc de données en mode caractère, les conversions suivantes sont réalisées :  
  
    |Sens de l'opération en bloc|Conversion|  
    |---------------------------------|----------------|  
    |Exporter|Convertit les données en représentation caractère. Si la demande est faite explicitement, les données sont converties vers la page de codes demandée pour les colonnes de caractères. Si aucune page de codes n'est spécifiée, les données de caractères sont converties à l'aide de la page de codes OEM de l'ordinateur client.|  
    |Importer|Convertit les données de caractères en représentation native si nécessaire, puis traduit les données de caractères de la page de codes du client vers la page de codes des colonnes cibles.|  
  
-   Pour éviter la perte de caractères étendus pendant la conversion, utilisez le format de caractères Unicode ou spécifiez une page de codes.  
  
-   Les données `sql_variant` stockées dans un fichier au format caractère sont enregistrées sans métadonnées. Chaque valeur de données est convertie au format `char` suivant les règles de conversion implicite des données. Importées dans une colonne `sql_variant`, les données sont importées au format `char`. Importées dans une colonne dont le type de données est différent de `sql_variant`, les données sont converties à partir du format `char` à l'aide de la conversion implicite. Pour plus d’informations sur la conversion de données, consultez [Conversion de types de données &#40;moteur de base de données&#41;](/sql/t-sql/data-types/data-type-conversion-database-engine).  
  
-   Le **bcp** utilitaire exportations `money` valeurs sous forme de fichiers de données au format caractère avec quatre chiffres après la virgule décimale et sans symboles de groupement des chiffres tels que des virgules de séparation. Par exemple, une colonne `money` contenant la valeur 1 234 567,123456 est exportée en bloc dans un fichier en tant que chaîne de caractères 1234567,1235.  
  
## <a name="command-options-for-character-format"></a>Options de commande pour le format caractère  
 Vous pouvez importer des données au format caractère dans une table à l’aide de l’utilitaire **bcp**, BULK INSERT ou INSERT... SELECT \* FROM OPENROWSET(BULK...). Si vous utilisez une commande **bcp** ou une instruction BULK INSERT, vous pouvez spécifier le format de données dans la ligne de commande. Pour une instruction INSERT ... SELECT * FROM OPENROWSET(BULK...), vous devez spécifier le format de données dans un fichier de format.  
  
 Le format caractère est pris en charge par les options de ligne de commande suivantes :  
  
|Command|Option|Description|  
|-------------|------------|-----------------|  
|**bcp**|**-c**|Provoque le **bcp** utilitaire à utiliser les données de type caractère.<sup> 1</sup>|  
|BULK INSERT|DATAFILETYPE **='char'**|Utilise le format caractère lors de l'importation en bloc des données.|  
  
 <sup>1</sup> pour charger le caractère (**- c**) les données dans un format compatible avec les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des clients, utilisez le **-V** basculer. Pour plus d’informations, consultez [Importer des données au format natif et caractère à partir de versions antérieures de SQL Server](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md).  
  
 Pour plus d’informations, consultez [Utilitaire bcp](../../tools/bcp-utility.md), [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) ou [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).  
  
> [!NOTE]  
>  Vous pouvez également spécifier le formatage par champ dans un fichier de format. Pour plus d’informations, consultez [Fichiers de format pour l’importation ou l’exportation de données &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).  
  
## <a name="examples"></a>Exemples  
 Les exemples ci-après indiquent comment exporter en bloc des données caractères à l’aide de l’utilitaire **bcp** et comment importer en bloc les mêmes données à l’aide de l’instruction BULK INSERT.  
  
### <a name="sample-table"></a>Exemple de table  
 Les exemples nécessitent la création d'une table **myTestCharData** dans l'exemple de base de données **AdventureWorks** d'après le schéma **dbo** . Avant de commencer, vous devez créer cette base de données. Pour ce faire, dans l'éditeur de requête SQL [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] , exécutez le code suivant :  
  
```  
USE AdventureWorks;  
GO  
CREATE TABLE myTestCharData (  
   Col1 smallint,  
   Col2 nvarchar(50),  
   Col3 nvarchar(50)  
   );   
```  
  
 Pour remplir cette table et afficher le contenu résultant, exécutez les instructions suivantes :  
  
```  
INSERT INTO myTestCharData(Col1,Col2,Col3)  
   VALUES(1,'DataField2','DataField3');  
INSERT INTO myTestCharData(Col1,Col2,Col3)  
   VALUES(2,'DataField2','DataField3');  
GO  
SELECT Col1,Col2,Col3 FROM myTestCharData  
  
```  
  
### <a name="using-bcp-to-bulk-export-character-data"></a>Utilisation de bcp pour exporter en bloc des données de caractères  
 Pour exporter des données de la table vers le fichier de données, utilisez **bcp** avec l’option **out** et les qualificateurs suivants :  
  
|Qualificateurs|Description|  
|----------------|-----------------|  
|**-c**|Spécifie le format caractère.|  
|**-t** `,`|Virgule (`,`) servant d'indicateur de fin de champ.<br /><br /> Remarque : La marque de fin de champ par défaut est le caractère de tabulation (\t). Pour plus d’informations, consultez [Spécifier des indicateurs de fin de champ et de fin de ligne &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md).|  
|**-T**|Spécifie que l'utilitaire **bcp** se connecte à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec une connexion approuvée qui utilise la sécurité intégrée. Si **-T** n’est pas spécifié, vous devez indiquer **-U** et **-P** pour vous connecter.|  
  
 L'exemple suivant exporte en bloc les données au format caractère de la table `myTestCharData` dans un nouveau fichier de données nommé `myTestCharData-c.Dat`, qui utilise la virgule (,) comme marque de fin de champ. À l'invite de commandes [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, entrez :  
  
```  
bcp AdventureWorks..myTestCharData out C:\myTestCharData-c.Dat -c -t, -T  
  
```  
  
### <a name="using-bulk-insert-to-bulk-import-character-data"></a>Utilisation de l'instruction BULK INSERT pour importer en bloc des données de caractères  
 L'exemple suivant utilise l'instruction BULK INSERT pour importer les données du fichier de données `myTestCharData-c.Dat` dans la table `myTestCharData` . Dans l'Éditeur de requête [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] , exécutez :  
  
```  
USE AdventureWorks;  
GO  
BULK INSERT myTestCharData   
   FROM 'C:\myTestCharData-c.Dat'   
   WITH (  
      DATAFILETYPE='char',  
      FIELDTERMINATOR=','  
   );   
GO  
SELECT Col1,Col2,Col3 FROM myTestCharData;  
GO  
  
```  
  
##  <a name="RelatedTasks"></a> Tâches associées  
 **Pour utiliser des formats de données pour l'importation ou l'exportation en bloc**  
  
-   [Importer des données au format natif et caractère à partir de versions antérieures de SQL Server](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [Utiliser le format natif pour importer ou exporter des données &#40;SQL Server&#41;](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Utiliser le format caractère Unicode pour importer ou exporter des données &#40;SQL Server&#41;](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Utiliser le format natif Unicode pour importer ou exporter des données &#40;SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
## <a name="see-also"></a>Voir aussi  
 [bcp Utility](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)   
 [Types de données &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)   
 [Importer des données au format natif et caractère à partir de versions antérieures de SQL Server](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
  
