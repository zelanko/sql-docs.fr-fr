---
title: Valeurs pour les déclarations &lt;xsd:simpleType&gt; | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- xsd:simpleType declarations
ms.assetid: 557b972d-3af9-40bf-8382-72b05c9de1c1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f0b24a9c02e38ba8165e015cdf8d1b107e64cbaf
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63193072"
---
# <a name="values-for-ltxsdsimpletypegt-declarations"></a>Valeurs pour les déclarations &lt;xsd:simpleType&gt;
  Le tableau suivant décrit les restrictions appliquées, sur la base de toutes les énumérations de types simples XSD reconnus.  
  
 De plus, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prend pas en charge l’utilisation de la valeur NaN dans les déclarations **\<xsd:simpleType>** . Les schémas incluant cette valeur sont rejetés par le serveur.  
  
|Type simple|Limitation|  
|-----------------|----------------|  
|`duration`|La partie année doit figurer dans la plage comprise<sup>^</sup>entre-2<sup>^</sup>31 et 2 31-1. Le mois, le jour, l'heure, la minute et la seconde doivent tous être compris dans la plage de 0 à 9999. La partie secondes possède trois chiffres supplémentaires de précision à droite de la virgule décimale.|  
|`dateTime`|La partie heure dans le sous-champ de fuseau horaire doit être comprise dans la plage acceptée de -14 à +14. La partie année doit figurer dans la plage comprise entre 1 et 9999. La partie mois doit figurer dans la plage comprise entre 1 et 12. La partie jour doit figurer dans la plage comprise entre 1 et 31 et doit être une date calendaire valide. Par exemple, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] détecte une date non valide telle que 1974-02-31 et retourne une erreur puisque le mois de février ne contient pas 31 jours.<br /><br /> Le composant seconde prend en charge une précision de 100 nanosecondes. L'indication de fuseau horaire est facultative.<br /><br /> SQL Server 2005 prenait en charge les années comprises dans la plage de -9999 à 9999. SQL Server prend maintenant en charge une plage d'années plus restreinte. Pour plus d’informations, consultez [comparer du XML typé et du XML](compare-typed-xml-to-untyped-xml.md)non typé.|  
|`date`|La partie année doit figurer dans la plage comprise entre 1 et 9999. La partie mois doit figurer dans la plage comprise entre 1 et 12. La partie jour doit figurer dans la plage comprise entre 1 et 31 et doit être une date calendaire valide. Par exemple, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] détecte une date non valide telle que 1974-02-31 et retourne une erreur puisque le mois de février ne contient pas 31 jours.<br /><br /> SQL Server 2005 prenait en charge les années comprises dans la plage de -9999 à 9999. SQL Server prend maintenant en charge une plage d'années plus restreinte. Pour plus d’informations, consultez [comparer du XML typé et du XML](compare-typed-xml-to-untyped-xml.md)non typé.|  
|`gYearMonth`|La partie année doit figurer dans la plage comprise entre -9999 et 9999.|  
|`gYear`|La partie année doit figurer dans la plage comprise entre -9999 et 9999.|  
|`gMonthDay`|La partie mois doit figurer dans la plage comprise entre 1 et 12. La partie jour doit figurer dans la plage comprise entre 1 et 31.|  
|`gDay`|La partie jour doit figurer dans la plage comprise entre 1 et 31.|  
|`gMonth`|La partie mois doit figurer dans la plage comprise entre 1 et 12.|  
|`decimal`|Les valeurs de ce type doivent être conformes au format du type numérique SQL. Ce type représente en interne la prise en charge des nombres jusqu'à un total de 38 chiffres, 10 de ces positions étant réservées à la précision fractionnelle.|  
|`float`|Les valeurs de ce type doivent être conformes au format du type `real` SQL.|  
|**double**|Les valeurs de ce type doivent être conformes au format du type `float` SQL.|  
|`string`|Les valeurs de ce type doivent être conformes au format du type `nvarchar(max)` SQL.|  
|`anyURI`|Les valeurs de ce type ne peuvent excéder 4 000 caractères Unicode.|  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifications et limitations relatives aux collections de schémas XML sur le serveur](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
