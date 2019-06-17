---
title: Enregistrements et champs fournis par le fournisseur | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- records-provided fields [ADO]
- provider-supplied fields [ADO]
ms.assetid: 77f95e0a-0cf2-411a-a792-593f77330fbd
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 2b7ce62ebedbd5d0622c8b69720f7153d7711a48
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66700442"
---
# <a name="records-and-provider-supplied-fields"></a>Enregistrements et champs fournis par le fournisseur
Quand un [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) objet est ouvert, sa source peut être la ligne actuelle d’ouvert [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md), une URL absolue ou une URL relative en association avec une ouverture [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet .  
  
 Si le **enregistrement** est ouvert à partir d’un **Recordset**, le **enregistrement** objet [champs](../../../ado/reference/ado-api/fields-collection-ado.md) collection contiendra tous les champs à partir de la  **Jeu d’enregistrements**, ainsi que tous les champs ajoutés par le fournisseur sous-jacent.  
  
 Le fournisseur peut insérer des champs supplémentaires utilisés comme caractéristiques supplémentaires de la **enregistrement**. Par conséquent, un **enregistrement** peuvent avoir des champs uniques pas dans le **Recordset** en entier ou un **enregistrement** dérivé d’une autre ligne de la **Recordset**.  
  
 Par exemple, toutes les lignes d’un **Recordset** dérivé d’un message électronique de source de données peut avoir des colonnes, telles que From, à et de l’objet. Un **enregistrement** dérivé qui **Recordset** aura les mêmes champs. Toutefois, le **enregistrement** peut avoir également d’autres champs uniques spécifiques au message représenté par cette **enregistrement**, telles que la pièce jointe et Cc (copie carbone).  
  
 Bien que le **enregistrement** objet et la ligne actuelle de la **Recordset** ont les mêmes champs, ils sont différents, car **enregistrement** et **Recordset**objets ont différentes méthodes et propriétés.  
  
 Un champ commun par les **enregistrement** et **Recordset** peut être modifié sur des objets. Toutefois, le champ ne peut pas être supprimé sur le **enregistrement** de l’objet, bien que le fournisseur sous-jacent peut prendre en charge la valeur de champ null.  
  
 Après le **enregistrement** est ouvert, vous pouvez ajouter par programmation des champs. Vous pouvez également supprimer des champs que vous avez ajoutés, mais vous ne pouvez pas supprimer les champs de l’original **Recordset**.  
  
 Vous pouvez également ouvrir le **enregistrement** objet directement à partir d’une URL. Dans ce cas, les champs ajoutés à la **enregistrement** dépendent du fournisseur sous-jacent. Actuellement, la plupart des fournisseurs ajoutent un ensemble de champs qui décrivent l’entité représentée par le **enregistrement**. Si l’entité est constituée d’un flux d’octets, tel qu’un fichier simple, un [Stream](../../../ado/reference/ado-api/stream-object-ado.md) objet peut généralement être ouvert à partir de la **enregistrement**.  
  
## <a name="special-fields-for-document-source-providers"></a>Les fournisseurs de champs spéciaux pour le Document Source  
 Une classe spéciale de fournisseurs, appelée *fournisseurs de source de document*, gère les dossiers et les documents. Quand un **enregistrement** objet qui représente un document ou un **Recordset** objet représente un dossier de documents, le fournisseur de source de document remplit ces objets avec un ensemble de champs qui décrivent unique caractéristiques du document à la place la valeur réelle de document lui-même. En règle générale, un champ contient une référence à la **Stream** qui représente le document.  
  
 Ces champs constituent une ressource **enregistrement** ou **recordset** et sont répertoriés pour les fournisseurs spécifiques qui les prennent en charge dans [annexe a : Fournisseurs](../../../ado/guide/appendixes/appendix-a-providers.md).  
  
 Index de deux constantes le **champs** collection d’une ressource **enregistrement** ou **Recordset** pour extraire une paire de champs couramment utilisés. Le **champ** objet [valeur](../../../ado/reference/ado-api/value-property-ado.md) propriété retourne le contenu souhaité.  
  
-   Le champ accédé avec la **adDefaultStream** constante contient un flux par défaut associé à la **enregistrement** ou **Recordset** objet. Le fournisseur affecte un flux par défaut à un objet.  
  
-   Le champ accédé avec la **adRecordURL** constante contient l’URL absolue qui identifie le document.  
  
 Un fournisseur de source de document ne prend pas en charge la [propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) collection de **enregistrement** et **champ** objets. Le contenu de la **propriétés** collection a la valeur null pour ces objets.  
  
 Un fournisseur de source de document peut ajouter une propriété spécifique au fournisseur comme **Type de source de données** pour déterminer si c’est un fournisseur de source de document. Pour plus d’informations sur la façon de déterminer le type de fournisseur, consultez la documentation du fournisseur.  
  
## <a name="resource-recordset-columns"></a>Colonnes de jeu d’enregistrements de ressources  
 Un *jeu d’enregistrements de ressource* se compose des colonnes suivantes.  
  
|Nom de colonne|type|Description|  
|-----------------|----------|-----------------|  
|RESOURCE_PARSENAME|AdVarWChar|En lecture seule. Indique l’URL de la ressource.|  
|RESOURCE_PARENTNAME|AdVarWChar|En lecture seule. Indique l’URL absolue de l’enregistrement parent.|  
|RESOURCE_ABSOLUTEPARSENAME|AdVarWChar|En lecture seule. Indique l’URL absolue de la ressource, qui est la concaténation de PARENTNAME et PARSENAME.|  
|RESOURCE_ISHIDDEN|AdBoolean|True si la ressource est masquée. Aucune ligne n’est retournée, sauf si la commande qui crée l’ensemble de lignes explicitement sélectionne les lignes où la propriété RESOURCE_ISHIDDEN a la valeur True.|  
|RESOURCE_ISREADONLY|AdBoolean|True si la ressource est en lecture seule. Tente d’ouvrir cette ressource avec DBBINDFLAG_WRITE et échoue avec DB_E_READONLY. Cette propriété peut être modifiée même lorsque la ressource n’a été ouverte pour la lecture.|  
|RESOURCE_CONTENTTYPE|AdVarWChar|Indique l’utilisation probable du document-par exemple, un dossier d’avocat. Cela peut correspondre au modèle Office ayant servi à créer le document.|  
|RESOURCE_CONTENTCLASS|AdVarWChar|Indique le type MIME du document, indiquant le format comme «`text/html`».|  
|RESOURCE_CONTENTLANGUAGE|AdVarWChar|Indique la langue dans laquelle le contenu est stocké.|  
|RESOURCE_CREATIONTIME|adFileTime|En lecture seule. Indique une structure FILETIME qui contient l’heure de que la ressource a été créée. L’heure est signalée dans le format de temps universel coordonné (UTC).|  
|RESOURCE_LASTACCESSTIME|AdFileTime|En lecture seule. Indique une structure FILETIME qui contient l’heure de dernier accès à la ressource. L’heure est au format UTC. Les membres FILETIME sont zéro si le fournisseur ne prend pas en charge ce membre de temps.|  
|RESOURCE_LASTWRITETIME|AdFileTime|En lecture seule. Indique une structure FILETIME qui contient l’heure de dernière écriture de la ressource. L’heure est au format UTC. Les membres FILETIME sont zéro si le fournisseur ne prend pas en charge ce membre de temps.|  
|RESOURCE_STREAMSIZE|asUnsignedBigInt|En lecture seule. Indique la taille du flux de valeur par défaut de la ressource, en octets.|  
|RESOURCE_ISCOLLECTION|AdBoolean|En lecture seule. True si la ressource est une collection, comme un répertoire. False si la ressource est un fichier simple.|  
|RESOURCE_ISSTRUCTUREDDOCUMENT|AdBoolean|True si la ressource est un document structuré. False si la ressource n’est pas un document structuré. Il peut être une collection ou un fichier simple.|  
|DEFAULT_DOCUMENT|AdVarWChar|En lecture seule. Indique que cette ressource contient une URL vers le document simple par défaut d’un dossier ou un document structuré. Utilisé lorsque le flux par défaut est demandé à partir d’une ressource. Cette propriété est vide pour un fichier simple.|  
|CHAPTERED_CHILDREN|adChapter|En lecture seule. Facultatif. Indique le chapitre de l’ensemble de lignes qui contient les enfants de la ressource. (Le *fournisseur OLE DB pour la publication Internet* n’utilise pas cette colonne.)|  
|RESOURCE_DISPLAYNAME|AdVarWChar|En lecture seule. Indique le nom complet de la ressource.|  
|RESOURCE_ISROOT|AdBoolean|En lecture seule. True si la ressource est la racine d’une collection ou un document structuré.|  
  
## <a name="see-also"></a>Voir aussi  
 [Enregistrement objet (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [Annexe A : fournisseurs](../../../ado/guide/appendixes/appendix-a-providers.md)
