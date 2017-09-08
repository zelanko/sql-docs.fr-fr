---
title: Restaurer des commandes (TMSL) | Documents Microsoft
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 360a1567-67ae-459d-8865-9a2bef8d4186
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1b03fce8372619208cc6f065ff4f2cf805efb5fb
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="restore-command-tmsl"></a>Restaurer des commandes (TMSL)

[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

  Restaure une base de données Analysis Services à partir d'un fichier de sauvegarde.  
  
## <a name="request"></a>Demande  
  
```  
    {  
"restore": {  
            "description": "Parameters of Restore command of Analysis Services JSON API",  
            "properties": {  
            "database": {  
                "type": "string"  
            },  
            "file": {  
                "type": "string"  
            },  
            "password": {  
                "type": "string"  
            },  
            "dbStorageLocation": {  
                "type": "string"  
            },  
            "allowOverwrite": {  
                "type":boolean  
            },  
            "readWriteMode": {  
                "enum": [  
                "readWrite",  
                "readOnly",  
                "readOnlyExclusive"  
                ]  
. . .   
```  
  
 **Restaurer** possède plusieurs propriétés.  
  
||||  
|-|-|-|  
|**Propriété**|**Default**|**Description**|  
|database|[Obligatoire]|Le nom de l’objet de base de données à restaurer.|  
|fichier|[Obligatoire]|Le fichier de sauvegarde nom/chemin d’accès.|  
|password|Vide|Le mot de passe à utiliser pour déchiffrer le fichier de sauvegarde.|  
|allowOverwrite|False|Valeur booléenne qui, si true, indique qu’un fichier de sauvegarde qui existe déjà sera écrasée ; Sinon, false.|  
|readWriteMode|Lecture/écriture|Valeur d’énumération qui indique les modes d’accès autorisés à la base de données.<br /><br /> **Les valeurs d’énumération sont comme suit :**<br /><br /> readWrite : l’accès en lecture-écriture est autorisé.<br /><br /> readOnly : accès en lecture seule est autorisé.<br /><br /> readOnlyExclusive – un accès exclusif en lecture seule est autorisé.|  
|dbStorageLocation|Vide|Emplacement de stockage pour la base de données restaurée.|  
  
## <a name="response"></a>Réponse  
 Retourne un résultat vide lorsque la commande aboutit. Sinon, une exception XMLA est retournée.  
  
## <a name="example"></a>Exemple  
 **Exemple 1** -restaurer une base de données à partir d’un dossier local.  
  
```  
{   
   "restore": {   
      "database":"AdventureWorksDW2014",  
      "file":"c:\\awdbdwfile.abf",  
      "security":"...",  
      "allowOverwrite":"true",  
      "password":"..",  
      "locations":"d:\\SQL Server Analysis Services\\data\\",  
      "storageLocation":".."  
   }  
}  
```  
  
## <a name="usage-endpoints"></a>Utilisation (points de terminaison)  
 Cet élément de commande est utilisé dans une instruction de la [méthode Execute &#40; XMLA &#41; ](../../analysis-services/xmla/xml-elements-methods-execute.md) appel via un point de terminaison XMLA exposée comme suit :  
  
-   Comme une fenêtre XMLA dans SQL Server Management Studio (SSMS)  
  
-   En tant que fichier d’entrée dans le **invoke-ascmd** applet de commande PowerShell  
  
-   En tant qu’entrée pour un travail de l’Agent SQL Server ou de tâche SSIS  
  
 Vous pouvez générer un script prêts à l’emploi pour cette commande à partir de SSMS en cliquant sur le bouton de Script dans la boîte de dialogue de restauration.  
  
 Le [ \[MS-SSAS-T\]: QL Server tabulaires Analysis Services (SQL Server technique Protocol)](http://go.microsoft.com/fwlink/p/?LinkId=784855) document inclut section 3.1.5.2.2 qui décrit la structure des objets et les commandes de métadonnées sous forme de tableau JSON. Actuellement, ce document traite des commandes et fonctions non encore implémentées dans un script TMSL. Reportez-vous à la rubrique [langage de script de modèle tabulaire &#40; TMSL &#41; Référence](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md) pour des explications sur ce qui est pris en charge  
  
## <a name="see-also"></a>Voir aussi  
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference [Informations de référence sur TMSL &#40;Tabular Model Scripting Language&#41;]](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Sauvegarde et restauration de bases de données Analysis Services](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
