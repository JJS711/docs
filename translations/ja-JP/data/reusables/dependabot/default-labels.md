---
ms.openlocfilehash: 3b05d1b75c37f24e9ae4ce03618910c572f259d1
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/05/2022
ms.locfileid: "145138827"
---
既定では、{% data variables.product.prodname_dependabot %} ではすべての pull request を `dependencies` ラベル付きで発行します。 複数のパッケージマネージャが定義されている場合、{% data variables.product.prodname_dependabot %}はそれぞれのPull Requestに追加のラベルを含めます。 これは、その pull request によってどの言語またはエコシステムが更新されるかを示します。たとえば、Gradle の更新には `java`、Git サブモジュールの更新には `submodules` というようになります。 {% data variables.product.prodname_dependabot %}は、リポジトリ中の必要に応じて自動的にこれらのデフォルトラベルを作成します。
