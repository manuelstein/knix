#   Copyright 2020 The KNIX Authors
#
#   Licensed under the Apache License, Version 2.0 (the "License");
#   you may not use this file except in compliance with the License.
#   You may obtain a copy of the License at
#
#       http://www.apache.org/licenses/LICENSE-2.0
#
#   Unless required by applicable law or agreed to in writing, software
#   distributed under the License is distributed on an "AS IS" BASIS,
#   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
#   See the License for the specific language governing permissions and
#   limitations under the License.

VERSION=$(shell git describe --long --tags --dirty --always)
PKG=MicroFunctions-$(VERSION).tgz
FILES=$(shell find microfunctions/)

default: $(PKG)

$(PKG): $(FILES)
	sed 's/^version:.*/version: $(VERSION)/' -i microfunctions/Chart.yaml
	rm -f $(PKG)
	helm dependency update microfunctions/
	helm package microfunctions/
	sed 's/^version:.*/version: auto/' -i microfunctions/Chart.yaml

