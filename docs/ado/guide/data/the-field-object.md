---
title: L’objet de champ | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Field object [ADO]
ms.assetid: 7d1c4ad5-4be3-42ab-b516-e7133ca300bc
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 80e6576b236db44452c4e89b1d8f3bb8976ab120
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67923983"
---
# <a name="the-field-object"></a>Field, objet
Chaque **champ** objet correspond généralement à une colonne dans une table de base de données. Toutefois, un **champ** peut également représenter un pointeur vers un autre **Recordset**, appelé un chapitre. Exceptions, telles que les colonnes de chapitres, seront abordées plus loin dans ce guide.  
  
 Utilisez le **valeur** propriété du **champ** objets pour définir ou retourner des données pour l’enregistrement en cours. Selon les fonctionnalités le fournisseur expose des regroupements, des méthodes ou propriétés d’un **champ** objet n’est peut-être pas disponible.  
  
 Avec les collections, les méthodes et les propriétés d’un **champ** de l’objet, vous pouvez procédez comme suit :  
  
-   Retourner le nom d’un champ à l’aide de la **nom** propriété.  
  
-   Afficher ou modifier les données dans le champ à l’aide de la **valeur** propriété. **Valeur** est la propriété par défaut de la **champ** objet.  
  
-   Retourner les caractéristiques de base d’un champ à l’aide de la **Type**, **précision**, et **NumericScale** propriétés.  
  
-   Renvoyer la taille déclarée d’un champ à l’aide de la **DefinedSize** propriété.  
  
-   Retourner la taille réelle des données dans un champ donné à l’aide de la **ActualSize** propriété.  
  
-   Déterminer les types de fonctionnalités sont prises en charge pour un champ donné à l’aide de la **attributs** propriété et **propriétés** collection.  
  
-   Manipuler les valeurs des champs contenant des données binaires ou caractères longues à l’aide de la **AppendChunk** et **GetChunk** méthodes.  
  
 Résoudre les différences dans les valeurs de champ au cours de la mise à jour par lot à l’aide de la **OriginalValue** et **UnderlyingValue** si le fournisseur prend en charge les mises à jour par lots, les propriétés.  
  
## <a name="describing-a-field"></a>Description d’un champ  
 Les rubriques suivantes abordent les propriétés de la [champ](../../../ado/reference/ado-api/field-object.md) objet qui représentent des informations qui décrivent le **champ** objet proprement dit : autrement dit, les métadonnées relatives au champ. Ces informations peuvent être utilisées pour déterminer une bonne partie du schéma de la **Recordset**. Ces propriétés incluent **Type**, **DefinedSize** et **ActualSize**, **nom**, et **NumericScale**et **précision**.  
  
### <a name="discovering-the-data-type"></a>Découvrir le Type de données  
 Le **Type** propriété indique le type de données du champ. Le type de données constantes énumérées qui sont pris en charge par ADO sont décrites dans [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md) dans le *de référence du programmeur ADO*.  
  
 Pour les types numériques tels de virgule flottante **adNumeric**, vous pouvez obtenir plus d’informations. Le **NumericScale** propriété indique le nombre de chiffres à droite de la virgule décimale sera utilisé pour représenter les valeurs pour le **champ**. Le **précision** propriété spécifie le nombre maximal de chiffres utilisés pour représenter les valeurs pour le **champ**.  
  
### <a name="determining-field-size"></a>Détermination de la taille de champ  
 Utilisez le **DefinedSize** propriété afin de déterminer la capacité de données d’un **champ** objet.  
  
 Utilisez le **ActualSize** propriété pour retourner la longueur réelle d’un **champ** valeur de l’objet. Pour tous les champs, les **ActualSize** propriété est en lecture seule. Si ADO ne peut pas déterminer la longueur de la **champ** valeur de l’objet, le **ActualSize** retourne de la propriété **adUnknown**.  
  
 Le **DefinedSize** et **ActualSize** propriétés ont des objectifs différents. Par exemple, considérez un **champ** objet avec un type déclaré de **adVarChar** et un **DefinedSize** valeur de propriété de 50, contenant un seul caractère. Le **ActualSize** valeur de propriété retournée est la longueur en octets du caractère unique.  
  
### <a name="determining-field-contents"></a>Déterminer le contenu du champ  
 L’identificateur de la colonne à partir de la source de données est représenté par le **nom** propriété de la **champ**. Le **valeur** propriété de la **champ** objet retourne ou définit le contenu des données réelles du champ. Il s’agit de la propriété par défaut.  
  
 Pour modifier les données dans un champ, définissez la **valeur** propriété égale à une nouvelle valeur du type correct. Type de curseur doit prendre en charge les mises à jour pour modifier le contenu d’un champ. Validation de la base de données n'est pas effectuée en mode batch, vous devez rechercher les erreurs lorsque vous appelez **UpdateBatch** dans ce cas. Certains fournisseurs prennent également en charge ADO **champ** l’objet **UnderlyingValue** et **OriginalValue** propriétés pour vous aider à résoudre les conflits lorsque vous tentez mises à jour par lots. Pour plus d’informations sur la façon de résoudre ces conflits, consultez [modification des données](../../../ado/guide/data/editing-data.md).  
  
> [!NOTE]
>  **Recordset Field** valeurs ne peuvent pas être définies lors de l’ajout de nouveaux **champs** à un **Recordset**. Au lieu de cela, nouvelle **champs** peuvent être ajoutés à un fermé **Recordset**. Le **Recordset** doit être ouvert et uniquement puis peuvent valeurs être assignées à ces **champs**.  
  
### <a name="getting-more-field-information"></a>Informations complémentaires sur le champ  
 Objets ADO possèdent deux types de propriétés : intégrées et dynamiques. À ce stade, seules les propriétés intégrées de la **champ** objet ont été abordés.  
  
 Propriétés intégrées sont les propriétés implémentées dans ADO et immédiatement disponibles pour tout nouvel objet, à l’aide du `MyObject.Property` syntaxe. Ils n’apparaissent pas en tant que **propriété** les objets d’un objet **propriétés** collection.  
  
 Propriétés dynamiques sont définies par le fournisseur de données sous-jacent et apparaissent dans le **propriétés** collection pour l’objet ADO approprié. Par exemple, une propriété spécifique au fournisseur peut indiquer si un **Recordset** objet prend en charge les transactions ou la mise à jour. Ces propriétés supplémentaires apparaissent en tant que **propriété** objets dans ce **Recordset** l’objet **propriétés** collection. Propriétés dynamiques peuvent être référencées uniquement par le biais de la collection, à l’aide de la syntaxe `MyObject.Properties(0)` ou `MyObject.Properties("Name")`.  
  
 Vous ne pouvez pas supprimer un de ces types de propriété.  
  
 Dynamique **propriété** objet possède quatre propriétés intégrées :  
  
-   Le **nom** propriété est une chaîne qui identifie la propriété.  
  
-   Le **Type** propriété est un entier qui spécifie le type de données de propriété.  
  
-   Le **valeur** propriété est une variante qui contient le paramètre de propriété. **Valeur** est la propriété par défaut pour un **propriété** objet.  
  
-   Le **attributs** propriété est un **Long** valeur qui indique les caractéristiques de la propriété spécifique au fournisseur.  
  
 Le **propriétés** collection pour le **champ** objet contient des métadonnées supplémentaires relatives au champ. Le contenu de cette collection varie en fonction du fournisseur. L’exemple de code suivant examine le **propriétés** collection de l’exemple **Recordset** présenté au début de cette section. Il examine tout d’abord le contenu de la collection. Ce code utilise le [fournisseur OLE DB pour SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md), la **propriétés** collection contient des informations relatives à ce fournisseur.  
  
```  
'BeginFieldProps  
    Dim objProp As ADODB.Property  
  
    For intLoop = 0 To (objFields.Count - 1)  
        Debug.Print objFields.Item(intLoop).Name  
  
        For Each objProp In objFields(intLoop).Properties  
            Debug.Print vbTab & objProp.Name & " = " & objProp.Value  
        Next objProp  
    Next intLoop  
'EndFieldProps  
```  
  
### <a name="dealing-with-binary-data"></a>Traitement des données binaires  
 Utilisez le [AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md) méthode sur un **champ** objet à remplir avec des données binaires ou caractères de long. Dans les situations où la mémoire système est limitée, vous pouvez utiliser la **AppendChunk** méthode pour manipuler les valeurs de type long dans les parties plutôt que dans leur intégralité.  
  
 Si le **adFldLong** bit dans le **attributs** propriété d’un **champ** objet est défini sur **True**, vous pouvez utiliser le  **AppendChunk** méthode pour ce champ.  
  
 La première **AppendChunk** appeler sur un **champ** objet écrit des données dans le champ, en remplaçant toutes les données existantes. Ultérieures **AppendChunk** appels ajoutent aux données existantes. Si vous ajoutez des données à un seul champ, et ensuite de définir ou de lire la valeur d’un autre champ dans l’enregistrement actif, ADO suppose que vous avez terminé d’ajouter des données dans le premier champ. Si vous appelez le **AppendChunk** méthode sur le premier champ, ADO interprète l’appel en tant que nouvelle **AppendChunk** opération et remplace les données existantes. L’accès à d’autres champs **Recordset** les objets qui ne sont pas des clones du premier **Recordset** n’interrompt pas les objets **AppendChunk** operations.  
  
 Utilisez le **GetChunk** méthode sur un **champ** objet à récupérer tout ou partie de ses données binaires ou caractères de long. Dans les situations où la mémoire système est limitée, vous pouvez utiliser la **GetChunk** méthode pour manipuler les valeurs de type long dans les parties, plutôt que dans leur intégralité.  
  
 Les données qui un **GetChunk** appel retourne est affectée à *variable*. Si *taille* est supérieur aux données restantes, le **GetChunk** méthode retourne uniquement les données restantes sans remplissage *variable* avec des espaces vides. Si le champ est vide, le **GetChunk** méthode retourne une valeur null.  
  
 Chaque **GetChunk** appel récupère les données en commençant à partir de laquelle le précédent **GetChunk** appel s’est arrêté. Toutefois, si vous récupérez des données à partir d’un champ et ensuite définissez ou lire la valeur d’un autre champ dans l’enregistrement actif, ADO part du principe que vous avez terminé la récupération des données à partir du premier champ. Si vous appelez le **GetChunk** méthode sur le premier champ, ADO interprète l’appel en tant que nouvelle **GetChunk** opération et commence à lire à partir du début des données. L’accès à d’autres champs **Recordset** les objets qui ne sont pas des clones du premier **Recordset** n’interrompt pas les objets **GetChunk** operations.  
  
 Si le **adFldLong** bit dans le **attributs** propriété d’un **champ** objet est défini sur **True**, vous pouvez utiliser le **GetChunk**  (méthode) pour ce champ.  
  
 S’il n’existe aucun enregistrement actif lorsque vous utilisez le **GetChunk** ou **AppendChunk** méthode sur un **champ** de l’objet, l’erreur 3021 (aucun enregistrement actif) survient.  
  
 Pour obtenir un exemple d’utilisation de ces méthodes pour manipuler des données binaires, consultez le [AppendChunk, méthode](../../../ado/reference/ado-api/appendchunk-method-ado.md) et [GetChunk, méthode](../../../ado/reference/ado-api/getchunk-method-ado.md) exemples dans le *de référence du programmeur ADO*.
