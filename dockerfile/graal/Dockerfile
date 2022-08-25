#
# Licensed to the Apache Software Foundation (ASF) under one
# or more contributor license agreements.  See the NOTICE file
# distributed with this work for additional information
# regarding copyright ownership.  The ASF licenses this file
# to you under the Apache License, Version 2.0 (the
# "License"); you may not use this file except in compliance
# with the License.  You may obtain a copy of the License at
#
#   http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing,
# software distributed under the License is distributed on an
# "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
# KIND, either express or implied.  See the License for the
# specific language governing permissions and limitations
# under the License.
#

FROM perftool/base:graal

RUN apt-get update && \
    apt-get install -y build-essential libz-dev zlib1g-dev && \
    /usr/lib/jvm/graalvm/bin/gu install native-image && \
    ln -s /usr/lib/jvm/graalvm/bin/native-image /usr/bin/native-image && \
    apt-get install -y maven && \
    apt-get clean all

# pre download some jar package
COPY pom.xml /opt/perf/pom.xml

RUN mvn clean package && \
    rm -rf pom.xml
