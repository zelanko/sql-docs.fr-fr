---
title: Correspondance automatique des paires de syntaxe | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [SQL Server], delimiter highlighting
- IntelliSense [SQL Server], syntax pair matching
ms.assetid: bfc54cda-bfd6-4545-a5b9-f9db2ae13769
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 530747edf03e9790c2f728ec5485d305da046d08
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66064153"
---
# <a name="automatic-matching-of-syntax-pairs"></a>Correspondance automatique des paires de syntaxe
  La correspondance automatique des paires de syntaxe vous informe immédiatement si les éléments syntaxiques qui doivent être codés par paire sont correctement assortis. Cette correspondance est connue comme correspondance des séparateurs dans l’éditeur de requête du [!INCLUDE[ssDE](../../includes/ssde-md.md)] , correspondance des accolades dans l’éditeur de requête XMLA Analysis Services et correspondance des parenthèses dans les éditeurs MDX et DMX.  
  
## <a name="database-engine-query-editor-delimiter-matching"></a>Correspondance des séparateurs dans l'éditeur de requête du moteur de base de données  
 L’éditeur de requête du [!INCLUDE[ssDE](../../includes/ssde-md.md)] correspond aux séparateurs qui identifient les limites des blocs de code. La correspondance est réalisée de deux façons :  
  
-   L'éditeur met en surbrillance les deux séparateurs d'une paire lorsque vous terminez de taper le second séparateur de la paire.  
  
-   Chaque fois que le curseur est dans l'un des séparateurs d'une paire, vous pouvez utiliser le raccourci clavier CTRL+] pour atteindre le séparateur correspondant.  
  
### <a name="delimiter-pairs"></a>Paires de séparateurs  
 La correspondance automatique des séparateurs reconnaît les jeux de séparateurs suivants :  
  
|Séparateur de début|Séparateur de fin|  
|--------------------|-----------------------|  
|**(**|**)**|  
|**BEGIN**|**END**|  
|**BEGIN TRY**|**END TRY**|  
|**BEGIN CATCH**|**END CATCH**|  
  
 La correspondance automatique des séparateurs ne reconnaît pas les séparateurs pour les identificateurs entre parenthèses ([ObjectName]) ou les identificateurs entre guillemets ("ObjectName"). La correspondance des paires ne fonctionne pas pour les séparateurs à guillemet simple des littéraux de chaîne ('chaîne') parce que le codage de couleur donne déjà une indication sur le fait que la chaîne a été délimitée ou pas.  
  
### <a name="delimiter-highlighting"></a>Mise en surbrillance de séparateurs  
 La correspondance met en surbrillance l'élément de début et l'élément de fin d'une paire de séparateurs. Vous pouvez ainsi identifier visuellement les blocs de code et rechercher les erreurs de paires de séparateurs.  
  
 Les séparateurs sont mis en surbrillance lorsque vous tapez la dernière lettre qui complète la paire. Par exemple, pour une paire BEGIN END où vous tapez d'abord BEGIN suivi de END, la mise en surbrillance s'active lorsque vous tapez la dernière lettre de END. Vous n'avez pas à taper le séparateur de début suivi du séparateur de fin pour activer la mise en surbrillance. Si vous tapez en premier END, puis faites défiler le script vers le haut et tapez BEGIN, la mise en surbrillance est activée lorsque vous tapez la dernière lettre de BEGIN. La dernière lettre tapée n'est pas forcément la dernière lettre du séparateur. Par exemple, si vous orthographiez mal BEGIN et tapez BEIN, lorsque vous insérez le G, la paire BEGIN END est mise en surbrillance.  
  
 La paire de séparateurs reste en surbrillance jusqu'à ce que vous déplaciez le curseur. La mise en surbrillance est désactivée lorsque le curseur est déplacé, même si la nouvelle position du curseur demeure dans le même séparateur. Vous pouvez réactiver la mise en surbrillance en supprimant et en retapant une lettre de l'un des membres de la paire.  
  
## <a name="analysis-services-xmla-query-editor-brace-matching"></a>Correspondance des accolades de l'éditeur de requête XMLA Analysis Services  
 La correspondance des accolades de l'éditeur de requête XMLA montre si vous avez fermé des éléments en mettant en surbrillance les accolades d'ouverture et de fermeture. Vous pouvez également utiliser le raccourci clavier CTRL+] pour passer d'une accolade à l'accolade correspondante.  
  
 L'éditeur de requête XMLA effectue la correspondance des accolades pour les termes suivants :  
  
-   Correspondance des balises de début et de fin.  
  
-   Toute paire de signes « inférieur à » (« \< ») et « supérieur à » (« > »).  
  
-   Début et fin des commentaires.  
  
-   Début et fin des instructions de traitement.  
  
-   Début et fin des blocs CDATA.  
  
-   Début et fin des déclarations DTD.  
  
-   Ouverture et fermeture des guillemets sur les attributs.  
  
## <a name="mdx-and-dmx-editor-parenthesis-matching"></a>Correspondance des parenthèses de l'éditeur MDX et DMX  
 Les éditeurs MDX (Multi-Dimensional Expressions) et DMX (Data Mining Expressions) font correspondre automatiquement les paires de parenthèses dans les fonctions.  
  
  
