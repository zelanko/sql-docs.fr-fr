---
title: Convertir des schémas XDR annotés en XSD (SQLXML)
description: Découvrez comment convertir un schéma XDR annoté en schéma XSD équivalent à l’aide de l’outil de conversion XDR vers XSD de SQLXML 4,0.
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XDR schemas, converting schemas
- annotated XSD schemas, converting schemas
- XDR to XSD Converter tool [SQLXML]
- XDR schemas [SQLXML], converting
- converting annotated schemas
- mapping schema [SQLXML], conversions
- XSD schemas [SQLXML], converting schemas
ms.assetid: 151c94a8-66d3-4c46-a5ff-a22df456940a
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d7936bf8d9d9c37620ef9b692c125ff16f1cea85
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97467110"
---
# <a name="converting-annotated-xdr-schemas-to-equivalent-xsd-schemas-sqlxml-40"></a>Conversion de schémas XDR annotés en schémas XSD équivalents (SQLXML 4.0)
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]
  Le langage XSD (XML Schema Definition) est le successeur du langage de définition de schéma XDR (XML-Data Reduced). Avec l'introduction de la prise en charge du langage XSD dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0, les nouveaux schémas annotés sont donc supposés être créés à l'aide de ce langage XSD. SQLXML 4.0 inclut un outil de conversion XDR vers XSD conçu pour vous aider à convertir vos schémas XDR annotés en schémas XSD équivalents.  
  
> [!IMPORTANT]  
>  Utilisez cet outil uniquement lorsque vous souhaitez convertir des schémas XDR annotés en XSD pour une utilisation avec SQLXML 4.0. Il ne s'agit pas d'un outil de conversion XDR vers XSD à usage général. Les schémas XSD convertis peuvent ne pas se comporter de la même façon que les schémas XDR d'origine en cas d'utilisation dans d'autres environnements.  
  
 Si le fichier XDR d'entrée spécifie l'encodage dans la déclaration XML, cela devient l'encodage du fichier de sortie XSD généré.  
  
 L'outil de conversion (Cvtschema.exe) est installé dans le dossier \Program Files\SQLXML 4.0\bin et exécuté à l'invite de commandes.  
  
 Voici la syntaxe générale :  
  
```  
cvtschema XDRFileName, [-y], [-w] [-?]  
```  
  
 Où :  
  
 XDRFileName  
 Est le nom du fichier XDR qui doit être converti en XSD. L'outil lit le fichier XDR d'entrée et crée un fichier de sortie XSD dans le répertoire de travail actif. Si le fichier d'entrée a une extension .xdr ou .xml, le fichier XSD de sortie est créé avec le même nom mais avec une extension .xsd. Si l’extension de nom de fichier d’entrée est différente de. XML ou. XDR (ou si l’extension est manquante), le fichier de sortie est créé avec le même nom et l’extension. xsd est ajoutée au nom du fichier d’entrée. Par exemple, si le nom de fichier XDR d'entrée est SampleFile.abc, le fichier XSD résultant est enregistré en tant que SampleFile.abc.xsd.  
  
 -y  
 (Facultatif) Remplace le fichier XSD existant par le fichier XSD généré par l'outil de conversion. Si l'indicateur n'est pas spécifié, l'outil vous invite à spécifier si vous souhaitez remplacer le fichier XSD existant et vous donne la possibilité de modifier le nom de fichier de sortie.  
  
 -w  
 (Facultatif) Retourne des avertissements récupérables générés durant le processus de conversion par l'outil. Par défaut, l'outil affiche les messages uniquement pour les erreurs irrécupérables.  
  
 -?  
 Retourne une liste d’options que vous pouvez spécifier avec **Cvtschema**, ainsi qu’une explication.  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage de types de données XSD à des types de données XPath &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-using/mapping-xsd-data-types-to-xpath-data-types-sqlxml-4-0.md)   
 [Annotations XSD &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-using/xsd-annotations-sqlxml-4-0.md)  
  
  
