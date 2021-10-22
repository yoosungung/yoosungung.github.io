<div id="intro">

# 아마존 주언어

이 문서에서는 상태 컴퓨터를 선언적으로 설명하는 데 사용되는 [JSON](https://tools.ietf.org/html/rfc8259)기반 언어에 대해 설명합니다. 따라서 정의된 상태 컴퓨터는 소프트웨어에 의해 실행될 수 있습니다. 이 문서에서는 소프트웨어를 "인터프리터"라고 합니다.

</div>

저작권 © 2016 Amazon.com 주식회사 또는 계열사.

본 약관에 따라 본 명세서 및 관련 문서 파일("사양")의 사본을 획득한 사람에게 는 다음 조건에 따라 사용, 복사, 게시 및/또는 배포할 수 있는 권한이 무료로 부여됩니다.

상기 저작권 고지 및 본 허가 통지는 사양의 모든 사본에 포함됩니다.

명세서의 복사본을 수정, 병합, 하위 라이선스 및/또는 판매할 수 없습니다.

이 사양은 가맹점의 보증, 특정 목적에 대한 적합성 및 침해를 포함하되 이에 국한되지 않는 어떠한 종류의 보증없이 "있는 바와 같이"제공됩니다. 어떠한 경우에도 저자 또는 저작권 소유자는 계약, 불법 행위 또는 기타 계약, 규정 또는 기타 의 어떠한 클레임, 손해 또는 기타 책임에 대해 책임을 지지 않습니다.

사양에 포함된 모든 샘플 코드는 달리 명시되지 않는 한 아파치 라이센스 버전 2.0에 따라 라이선스가 부여됩니다.

<div id="toc">

<div>

## 내용물 표

*   상태 기계의 구조

    *   [](https://states-language.net/spec.html#example)

        [예: 헬로 월드](https://states-language.net/spec.html#example)

        [](https://states-language.net/spec.html#example)
    *   [](https://states-language.net/spec.html#toplevelfields)

        [최상위 필드](https://states-language.net/spec.html#toplevelfields)

        [](https://states-language.net/spec.html#toplevelfields)
*   개념

    *   [](https://states-language.net/spec.html#states-fields)

        [상태](https://states-language.net/spec.html#states-fields)

        [](https://states-language.net/spec.html#states-fields)
    *   [](https://states-language.net/spec.html#transition)

        [전환](https://states-language.net/spec.html#transition)

        [](https://states-language.net/spec.html#transition)
    *   [](https://states-language.net/spec.html#timestamps)

        [타임 스탬프](https://states-language.net/spec.html#timestamps)

        [](https://states-language.net/spec.html#timestamps)
    *   [](https://states-language.net/spec.html#data)

        [데이터](https://states-language.net/spec.html#data)

        [](https://states-language.net/spec.html#data)
    *   [](https://states-language.net/spec.html#context-object)

        [컨텍스트 개체](https://states-language.net/spec.html#context-object)

        [](https://states-language.net/spec.html#context-object)
    *   [](https://states-language.net/spec.html#path)

        [경로](https://states-language.net/spec.html#path)

        [](https://states-language.net/spec.html#path)
    *   [](https://states-language.net/spec.html#ref-paths)

        [참조 경로](https://states-language.net/spec.html#ref-paths)

        [](https://states-language.net/spec.html#ref-paths)
    *   [](https://states-language.net/spec.html#payload-template)

        [페이로드 템플릿](https://states-language.net/spec.html#payload-template)

        [](https://states-language.net/spec.html#payload-template)
    *   [](https://states-language.net/spec.html#intrinsic-functions)

        [본질적인 기능](https://states-language.net/spec.html#intrinsic-functions)

        [](https://states-language.net/spec.html#intrinsic-functions)
    *   [](https://states-language.net/spec.html#filters)

        [입력 및 출력 처리](https://states-language.net/spec.html#filters)

        [](https://states-language.net/spec.html#filters)
    *   [](https://states-language.net/spec.html#errors)

        [오류](https://states-language.net/spec.html#errors)

        [](https://states-language.net/spec.html#errors)
*   상태 유형

    *   [](https://states-language.net/spec.html#state-type-table)

        [상태 유형 및 필드 테이블](https://states-language.net/spec.html#state-type-table)

        [](https://states-language.net/spec.html#state-type-table)
    *   [](https://states-language.net/spec.html#pass-state)

        [패스 스테이트](https://states-language.net/spec.html#pass-state)

        [](https://states-language.net/spec.html#pass-state)
    *   [](https://states-language.net/spec.html#task-state)

        [작업 상태](https://states-language.net/spec.html#task-state)

        [](https://states-language.net/spec.html#task-state)
    *   [](https://states-language.net/spec.html#choice-state)

        [선택 상태](https://states-language.net/spec.html#choice-state)

        [](https://states-language.net/spec.html#choice-state)
    *   [](https://states-language.net/spec.html#wait-state)

        [대기 상태](https://states-language.net/spec.html#wait-state)

        [](https://states-language.net/spec.html#wait-state)
    *   [](https://states-language.net/spec.html#succeed-state)

        [성공 상태](https://states-language.net/spec.html#succeed-state)

        [](https://states-language.net/spec.html#succeed-state)
    *   [](https://states-language.net/spec.html#fail-state)

        [실패 상태](https://states-language.net/spec.html#fail-state)

        [](https://states-language.net/spec.html#fail-state)
    *   [](https://states-language.net/spec.html#parallel-state)

        [병렬 상태](https://states-language.net/spec.html#parallel-state)

        [](https://states-language.net/spec.html#parallel-state)
    *   [](https://states-language.net/spec.html#map-state)

        [지도 상태](https://states-language.net/spec.html#map-state)

        [](https://states-language.net/spec.html#map-state)
*   부록

    *   [](https://states-language.net/spec.html#appendix-a)

        [부록 A: 미리 정의된 오류 코드](https://states-language.net/spec.html#appendix-a)

        [](https://states-language.net/spec.html#appendix-a)
    *   [](https://states-language.net/spec.html#appendix-b)

        [부록 B: 본질적인 기능 목록](https://states-language.net/spec.html#appendix-b)

        [](https://states-language.net/spec.html#appendix-b)
*   문서 기록

    *   [](https://states-language.net/spec.html#2020-08-11)

        [2020년 8월 11일](https://states-language.net/spec.html#2020-08-11)

        [](https://states-language.net/spec.html#2020-08-11)

</div>

</div>

<div id="structure">

## 상태 기계의 구조

상태 컴퓨터는 [JSON 개체로](https://tools.ietf.org/html/rfc8259#section-4)표시됩니다.

### 예: 헬로 월드

상태 컴퓨터의 작업은 JSON 개체로 표시되는 상태, 최상위 "상태" 개체의 필드에 의해 지정됩니다. 이 예제에서는 "Hello World"라는 한 가지 상태가 있습니다.

    {
        "Comment": "A simple minimal example of the States language",
        "StartAt": "Hello World",
        "States": {
        "Hello World": {
          "Type": "Task",
          "Resource": "arn:aws:lambda:us-east-1:123456789012:function:HelloWorld",
          "End": true
        }
      }
    }

이 상태 컴퓨터가 시작되면 인터프리터는 시작 상태를 식별하여 실행을 시작합니다. 해당 상태를 실행한 다음 상태를 종료 상태로 표시하는지 확인합니다. 이 경우 기기가 종료되고 결과를 반환합니다. 상태가 종료 상태가 아닌 경우 인터프리터는 다음에 실행할 상태를 결정하기 위해 "다음" 필드를 찾습니다. 터미널 상태(성공, 실패 또는 종료 [상태)에](https://states-language.net/spec.html#terminal-state) 도달하거나 런타임 오류가 발생할 때까지 이 프로세스를 반복합니다.

이 예제에서는 기기에 "Hello World"라는 단일 상태가 포함되어 있습니다. "Hello World"는 작업 상태이므로 통역사가 작업 상태이므로 이를 실행하려고 합니다. "리소스" 필드의 값을 살펴보면 람다 함수를 가리키므로 통역사가 해당 함수를 호출하려고 시도합니다. Lambda 함수가 성공적으로 실행되면 컴퓨터가 성공적으로 종료됩니다.

상태 컴퓨터는 JSON 개체로 표시됩니다.

### 최상위 필드

상태 컴퓨터는 필드가 상태를 나타내는 "상태"라는 개체 필드가 있어야 합니다.

상태 컴퓨터에는 "StartAt"라는 문자열 필드가 있어야 하며, 값은 "상태" 필드의 이름 중 하나와 정확히 일치해야 합니다. 인터프리터는 지정된 상태에서 컴퓨터를 실행하기 시작합니다.

상태 컴퓨터에 사람이 읽을 수 있는 설명을 위해 제공된 "주석"이라는 문자열 필드가 있을 수 있습니다.

상태 컴퓨터에 사용되는 상태 언어의 버전을 제공하는 "버전"이라는 문자열 필드가 있을 수 있습니다. 이 문서에서는 버전 1.0에 대해 설명하며 생략된 경우 "버전"의 기본 값은 문자열 "1.0"입니다.

<font _mstmutation="1" _msthash="250081" _msttexthash="3270739160">상태 컴퓨터에는 "TimeoutSeconds"라는 정수 필드가 있을 수 있습니다. 제공된 경우 기기를 실행할 수 있는 최대 초 수를 제공합니다. 컴퓨터가 지정된 시간보다 오래 실행되면 통역사가 [오류 이름으로](https://states-language.net/spec.html#error-names)컴퓨터에 실패합니다.</font>`States.Timeout`

</div>

<div id="body">

## 개념

### 상태

상태는 최상위 "상태" 개체의 필드로 표시됩니다. 길이가 128개 유니코드 문자보다 작거나 같아야 하는 상태 이름은 필드 이름입니다. 상태 이름은 전체 상태 컴퓨터의 범위 내에서 고유해야 합니다. 상태는 작업(작업 단위)을 설명하거나 흐름 제어(예: Choice)를 지정합니다.

다음은 람다 함수를 실행하는 예제 상태입니다.

    "HelloWorld": {
      "Type": "Task",
      "Resource": "arn:aws:lambda:us-east-1:123456789012:function:HelloWorld",
      "Next": "NextState",
      "Comment": "Executes the HelloWorld Lambda function"
    }

참고:

1.  모든 주에는 "유형" 필드가 있어야 합니다. 이 문서에서는 이 필드의 값을 상태의 _형식으로,_위의 예제와 같은 상태를 작업 상태로 지칭합니다.

2.  모든 주에는 사람이 읽을 수 있는 의견이나 설명을 보유하기 위해 "주석" 필드가 있을 수 있습니다.

3.  대부분의 상태 유형에는 이 문서에 지정된 대로 추가 필드가 필요합니다.

4.  <font _mstmutation="1" _msthash="252733" _msttexthash="1115594220">선택, 성공 및 실패를 제외한 모든 주에는 가치가 부울 수 있어야 하는 "끝"이라는 필드가 있을 수 있습니다. "터미널 상태"라는 용어는 .</font>`{ "End": true }``{ "Type": "Succeed" }``{ "Type": "Fail" }`

### 전환

전환은 상태를 함께 연결하여 상태 컴퓨터에 대한 제어 흐름을 정의합니다. 터미널이 아닌 상태를 실행한 후 인터프리터는 다음 상태로의 전환을 따릅니다. 대부분의 상태 형식의 경우 전환은 무조건적이며 상태의 "Next" 필드를 통해 지정됩니다.

모든 비터미널 상태는 선택 상태를 제외한 "다음" 필드가 있어야 합니다. "Next" 필드의 값은 다른 상태의 이름과 정확히 일치해야 합니다.

주에서는 다른 주에서 여러 차례 전환할 수 있습니다.

### 타임 스탬프

선택 및 대기 상태는 타임스탬프를 나타내는 JSON 필드 값을 처리합니다. 이들은 ISO 8601의 [RFC3339](https://www.ietf.org/rfc/rfc3339.txt) 프로파일을 준수해야 하는 문자열이며, 대문자 "T" 문자가 날짜와 시간을 구분하는 데 사용해야 하는 추가 제한 사항과 함께"2016-03-14T011:59:00Z"와 같은 숫자 표준 시간대 오프셋이 없는 경우 대문자 "Z" 문자가 있어야 합니다.

### 데이터

인터프리터는 계산을 수행하거나 상태 컴퓨터의 흐름을 동적으로 제어하기 위해 상태 간에 데이터를 전달합니다. 이러한 모든 데이터는 JSON에 표현되어야 합니다.

<font _mstmutation="1" _msthash="117052" _msttexthash="11598784834">상태 컴퓨터가 시작되면 호출자는 초기 [JSON 텍스트를](https://tools.ietf.org/html/rfc8259#section-2) 입력으로 제공할 수 있으며, 이 텍스트를 입력으로 컴퓨터의 시작 상태로 전달합니다. 입력이 제공되지 않으면 기본값은 빈 JSON 개체입니다. 각 상태가 실행되면 JSON 텍스트를 입력으로 수신하고 JSON 텍스트여야 하는 임의출력을 생성할 수 있습니다. 두 상태가 전환에 의해 연결되면 첫 번째 상태의 출력이 두 번째 상태로 입력으로 전달됩니다. 기계의 터미널 상태의 출력은 출력으로 처리됩니다.</font> `{}`

예를 들어 두 숫자를 함께 추가하는 간단한 상태 컴퓨터를 고려하십시오.

    {
      "StartAt": "Add",
      "States": {
        "Add": {
          "Type": "Task",
          "Resource": "arn:aws:lambda:us-east-1:123456789012:function:Add",
          "End": true
        }
      }
    }

"추가" 람다 함수가 다음과 같이 정의되어 있다고 가정합니다.

    exports.handler = function(event, context) {
      context.succeed(event.val1 + event.val2);
    };

<font _mstmutation="1" _msthash="116519" _msttexthash="553283887">그런 다음 이 상태 컴퓨터가 입력으로 시작된 경우 출력은 숫자로 구성된 JSON 텍스트입니다.</font>`{ "val1": 3, "val2": 4 }``7`

JSON 인코딩 된 데이터에 적용되는 일반적인 제약 조건이 적용됩니다. 특히 다음 사항에 유의하십시오.

1.  JSON의 숫자는 일반적으로 이중 정밀도 IEEE-854 값에 해당하는 자바스크립트 의미 체계를 준수합니다. 이 및 기타 상호 운용성 우려는 [RFC 8259를](https://tools.ietf.org/html/rfc8259)참조하십시오.

2.  독립 실행형 "제한 문자열, 부울 및 숫자는 유효한 JSON 텍스트입니다.

### 컨텍스트 개체

인터프리터는 실행 상태 컴퓨터에 실행 및 기타 구현 세부 정보에 대한 정보를 제공할 수 있습니다. 이는 "컨텍스트 개체"라는 JSON 개체의 형태로 전달됩니다. 이 버전의 상태 언어 사양은 컨텍스트 개체의 내용을 지정하지 않습니다.

### 경로

경로는 JSON 텍스트로 구성 요소를 식별하는 데 사용되는 "$"로 시작하는 문자열입니다. 구문은 [JsonPath의 구문입니다.](https://github.com/jayway/JsonPath)

When a Path begins with "$", two dollar signs, this signals that it is intended to identify content within the Context Object. The first dollar sign is stripped, and the remaining text, which begins with a dollar sign, is interpreted as the JSONPath applying to the Context Object.

### Reference Paths

A Reference Path is a Path with syntax limited in such a way that it can only identify a single node in a JSON structure: The operators "@", ",", ":", and "?" are not supported - all Reference Paths MUST be unambiguous references to a single value, array, or object (subtree).

For example, if state input data contained the values:

    {
        "foo": 123,
        "bar": ["a", "b", "c"],
        "car": {
            "cdr": true
        }
    }

Then the following Reference Paths would return:

    $.foo => 123
    $.bar => ["a", "b", "c"]
    $.car.cdr => true

Paths and Reference Paths are used by certain states, as specified later in this document, to control the flow of a state machine or to configure a state's settings or options.

Here are some examples of acceptable Reference Path syntax:

    $.store.book
    $.store\.book
    $.\stor\e.boo\k
    $.store.book.title
    $.foo.\.bar
    $.foo\@bar.baz\[\[.\?pretty
    $.&Ж中.\uD800\uDF46
    $.ledgers.branch[0].pending.count
    $.ledgers.branch[0]
    $.ledgers[0][22][315].foo
    $['store']['book']
    $['store'][0]['book']

### Payload Template

A state machine interpreter dispatches data as input to tasks to do useful work, and receives output back from them. It is frequently desired to reshape input data to meet the format expectations of tasks, and similarly to reshape the output coming back. A JSON object structure called a Payload Template is provided for this purpose.

In the Task, Map, Parallel, and Pass States, the Payload Template is the value of a field named "Parameters". In the Task, Map, and Parallel States, there is another Payload Template which is the value of a field named "ResultSelector".

A Payload Template MUST be a JSON object; it has no required fields. The interpreter processes the Payload Template as described in this section; the result of that processing is called the payload.

To illustrate by example, the Task State has a field named "Parameters" whose value is a Payload Template. Consider the following Task State:

    "X": {
      "Type": "Task",
      "Resource": "arn:aws:states:us-east-1:123456789012:task:X",
      "Next": "Y",
      "Parameters": {
        "first": 88,
        "second": 99
      }
    }

In this case, the payload is the object with "first" and "second" fields whose values are respectively 88 and 99\. No processing needs to be performed and the payload is identical to the Payload Template.

Values from the Payload Template’s input and the Context Object can be inserted into the payload with a combination of a field-naming convention, Paths and Intrinsic Functions.

If any field within the Payload Template (however deeply nested) has a name ending with the characters ".$", its value is transformed according to rules below and the field is renamed to strip the ".$" suffix.

If the field value begins with only one "$", the value MUST be a Path. In this case, the Path is applied to the Payload Template’s input and is the new field value.

If the field value begins with "$", the first dollar sign is stripped and the remainder MUST be a Path. In this case, the Path is applied to the Context Object and is the new field value.

If the field value does not begin with "$", it MUST be an Intrinsic Function (see below). The interpreter invokes the Intrinsic Function and the result is the new field value.

If the path is legal but cannot be applied successfully, the interpreter fails the machine execution with an Error Name of "States.ParameterPathFailure". If the Intrinsic Function fails during evaluation, the interpreter fails the machine execution with an Error Name of "States.IntrinsicFailure".

A JSON object MUST NOT have duplicate field names after fields ending with the characters ".$" are renamed to strip the ".$" suffix.

    "X": {
      "Type": "Task",
      "Resource": "arn:aws:states:us-east-1:123456789012:task:X",
      "Next": "Y",
      "Parameters": {
        "flagged": true,
        "parts": {
          "first.$": "$.vals[0]",
          "last3.$": "$.vals[-3:]"
        },
        "weekday.$": "$.DayOfWeek",
        "formattedOutput.$": "States.Format('Today is {}', $.DayOfWeek)"
      }
    }

Suppose that the input to the P is as follows:

    {
      "flagged": 7,
      "vals": [0, 10, 20, 30, 40, 50]
    }

Further, suppose that the Context Object is as follows:

    {
      "DayOfWeek": "TUESDAY"
    }

In this case, the effective input to the code identified in the "Resource" field would be as follows:

    {
      "flagged": true,
      "parts": {
        "first": 0,
        "last3": [30, 40, 50]
      },
      "weekday": "TUESDAY",
      "formattedOutput": "Today is TUESDAY"
    }

### Intrinsic Functions

The States Language provides a small number of "Intrinsic Functions", constructs which look like functions in programming languages and can be used to help Payload Templates process the data going to and from Task Resources. See [Appendix B](https://states-language.net/spec.html#appendix-b) for a full list of Intrinsic Functions

Here is an example of an an Intrinsic Function named "States.Format" being used to prepare data:

    "X": {
      "Type": "Task",
      "Resource": "arn:aws:states:us-east-1:123456789012:task:X",
      "Next": "Y",
      "Parameters": {
        "greeting.$": "States.Format('Welcome to {} {}\\'s playlist.', $.firstName, $.lastName)"
      }
    }

1.  An Intrinsic Function MUST be a string.

2.  The Intrinsic Function MUST begin with an Intrinsic Function name. An Intrinsic Function name MUST contain only the characters A through Z, a through z, 0 through 9, ".", and "_".

    All Intrinsic Functions defined by this specification have names that begin with "States.". Other implementations may define their own Intrinsic Functions whose names MUST NOT begin with "States.".

3.  The Intrinsic Function name MUST be followed immediately by a list of zero or more arguments, enclosed by "(" and ")", and separated by commas.

4.  <font _mstmutation="1" _msthash="342134" _msttexthash="10086323">Intrinsic Function arguments may be strings enclosed by apostrophe () characters, numbers, null, Paths, or nested Intrinsic Functions.</font>`'`

5.  The value of a string, number or null argument is the argument itself. The value of an argument which is a Path is the result of applying it to the input of the Payload Template. The value of an argument which is an Intrinsic Function is the result of the function invocation."

    <font _mstmutation="1" _msthash="342433" _msttexthash="7889947">Note that in the example above, the first argument of could have been a Path that yielded the formatting template string.</font>`States.Format`

6.  The following characters are reserved for all Intrinsic Functions and MUST be escaped: ' { } \

    If any of the reserved characters needs to appear as part of the value without serving as a reserved character, it MUST be escaped with a backslash.

    If the character "\" needs to appear as part of the value without serving as an escape character, it MUST be escaped with a backslash.

    <font _mstmutation="1" _msthash="342849" _msttexthash="8942752">The literal string represents .  
    The literal string represents .  
    The literal string represents .  
    The literal string represents .</font> `\'``'``\{``{``\}``}``\\``\`

    In JSON, all backslashes contained in a string literal value must be escaped with another backslash, therefore, the above will equate to:

    <font _mstmutation="1" _msthash="343083" _msttexthash="8875984">The escaped string represents .  
    The escaped string represents .  
    The escaped string represents .  
    The escaped string represents .</font> `\\'``'``\\{``{``\\}``}``\\\\``\`

    <font _mstmutation="1" _msthash="343200" _msttexthash="6397612">If an open escape backslash is found in the Intrinsic Function, the interpreter will throw a runtime error.</font> `\`

### Input and Output Processing

As described above, data is passed between states as JSON texts. However, a state may want to process only a subset of its input data, and may want that data structured differently from the way it appears in the input. Similarly, it may want to control the format and content of the data that it passes on as output.

Fields named "InputPath", "Parameters", "ResultSelector", "ResultPath", and "OutputPath" exist to support this.

Any state except for the Fail and Succeed States MAY have "InputPath" and "OutputPath".

States which potentially generate results MAY have "Parameters", "ResultSelector" and "ResultPath": Task State, Parallel State, and Map State.

Pass State MAY have "Parameters" and "ResultPath" to control its output value.

#### Using InputPath, Parameters, ResultSelector, ResultPath and OutputPath

In this discussion, "raw input" means the JSON text that is the input to a state. "Result" means the JSON text that a state generates, for example from external code invoked by a Task State, the combined result of the branches in a Parallel or Map State, or the Value of the "Result" field in a Pass State. "Effective input" means the input after the application of InputPath and Parameters, "effective result" means the result after processing it with ResultSelector and "effective output" means the final state output after processing the result with ResultSelector, ResultPath and OutputPath.

1.  The value of "InputPath" MUST be a Path, which is applied to a State’s raw input to select some or all of it; that selection is used by the state, for example in passing to Resources in Task States and Choices selectors in Choice States.

2.  The value of "Parameters" MUST be a Payload Template which is a JSON object, whose input is the result of applying the InputPath to the raw input. If the "Parameters" field is provided, its payload, after the extraction and embedding, becomes the effective input.

3.  The value of "ResultSelector" MUST be a Payload Template, whose input is the result, and whose payload replaces and becomes the effective result.

4.  The value of "ResultPath" MUST be a Reference Path, which specifies the raw input’s combination with or replacement by the state’s result.

    The value of "ResultPath" MUST NOT begin with "$"; i.e. it may not be used to insert content into the Context Object.

5.  The value of "OutputPath" MUST be a Path, which is applied to the state’s output after the application of ResultPath, producing the effective output which serves as the raw input for the next state.

Note that JsonPath can yield multiple values when applied to an input JSON text. For example, given the text:

    { "a": [1, 2, 3, 4] }

<font _mstmutation="1" _msthash="117624" _msttexthash="24943542">Then if the JsonPath is appplied, the result will be two JSON texts, and . When this happens, to produce the effective input, the interpreter gathers the texts into an array, so in this example the state would see the input:</font>`$.a[0,1]``1``2`

    [ 1, 2 ]

The same rule applies to OutputPath processing; if the OutputPath result contains multiple values, the effective output is a JSON array containing all of them.

The "ResultPath" field’s value is a Reference Path that specifies where to place the result, relative to the raw input. If the raw input has a field at the location addressed by the ResultPath value then in the output that field is discarded and overwritten by the state's result. Otherwise, a new field is created in the state output, with intervening fields constructed as necessary. For example, given the raw input:

    {
      "master": {
        "detail": [1, 2, 3]
      }
    }

<font _mstmutation="1" _msthash="117091" _msttexthash="6686628">If the state's result is the number , and the "ResultPath" is , then in the output the field would be overwritten:</font>`6``$.master.detail``detail`

    {
      "master": {
        "detail": 6
      }
    }

<font _mstmutation="1" _msthash="117351" _msttexthash="10032412">If instead a "ResultPath" of was used then the result would be combined with the raw input, producing a chain of new fields containing and :</font>`$.master.result.sum``result``sum`

    {
      "master": {
        "detail": [1, 2, 3],
        "result": {
          "sum": 6
        }
      }
    }

<font _mstmutation="1" _msthash="117611" _msttexthash="23087779">If the value of InputPath is , that means that the raw input is discarded, and the effective input for the state is an empty JSON object, . Note that having a value of is different from the "InputPath" field being absent.</font>`null``{}``null`

<font _mstmutation="1" _msthash="117741" _msttexthash="12840074">If the value of ResultPath is , that means that the state’s result is discarded and its raw input becomes its result.</font>`null`

<font _mstmutation="1" _msthash="117871" _msttexthash="10349495">If the value of OutputPath is , that means the input and result are discarded, and the effective output from the state is an empty JSON object, .</font>`null``{}`

#### Defaults

Each of InputPath, Parameters, ResultSelector, ResultPath, and OutputPath are optional. The default value of InputPath is "$", so by default the effective input is just the raw input. The default value of ResultPath is "$", so by default a state’s result overwrites and replaces the input. The default value of OutputPath is "$", so by default a state’s effective output is the result of processing ResultPath.

Parameters and ResultSelector have no default value. If absent, they have no effect on their input.

Therefore, if none of InputPath, Parameters, ResultSelector, ResultPath, or OutputPath are supplied, a state consumes the raw input as provided and passes its result to the next state.

#### Input/Output Processing Examples

<font _mstmutation="1" _msthash="117468" _msttexthash="8180757">Consider the example given above, of a Lambda task that sums a pair of numbers. As presented, its input is: and its output is: .</font>`{ "val1": 3, "val2": 4 }``7`

Suppose the input is little more complex:

    {
      "title": "Numbers to add",
      "numbers": { "val1": 3, "val2": 4 }
    }

Then suppose we modify the state definition by adding:

    "InputPath": "$.numbers",
    "ResultPath": "$.sum"

<font _mstmutation="1" _msthash="118118" _msttexthash="23566192">And finally,suppose we simplify Line 4 of the Lambda function to read as follows: . This is probably a better form of the function, which should really only care about doing math and not care how its result is labeled.</font>`return JSON.stringify(total)`

In this case, the output would be:

    {
      "title": "Numbers to add",
      "numbers": { "val1": 3, "val2": 4 },
      "sum": 7
    }

The interpreter might need to construct multiple levels of JSON object to achieve the desired effect. Suppose the input to some Task State is:

    { "a": 1 }

Suppose the output from the Task is "Hi!", and the value of the "ResultPath" field is "$.b.greeting". Then the output from the state would be:

    {
      "a": 1,
      "b": {
        "greeting": "Hi!"
      }
    }

#### Runtime Errors

<font _mstmutation="1" _msthash="130676" _msttexthash="24256843">Suppose a state’s input is the string , and its "ResultPath" field has the value "$.x". Then ResultPath cannot apply and the interpreter fails the machine with an Error Name of "States.ResultPathMatchFailure".</font>`"foo"`

### Errors

Any state can encounter runtime errors. Errors can arise because of state machine definition issues (e.g. the "ResultPath" problem discussed immediately above), task failures (e.g. an exception thrown by a Lambda function) or because of transient issues, such as network partition events.

When a state reports an error, the default course of action for the interpreter is to fail the whole state machine.

#### Error representation

Errors are identified by case-sensitive strings, called Error Names. The States language defines a set of built-in strings naming well-known errors, all of which begin with the prefix "States."; see [Appendix A](https://states-language.net/spec.html#appendix-a).

States MAY report errors with other names, which MUST NOT begin with the prefix "States.".

#### Retrying after error

Task States, Parallel States, and Map States MAY have a field named "Retry", whose value MUST be an array of objects, called Retriers.

Each Retrier MUST contain a field named "ErrorEquals" whose value MUST be a non-empty array of Strings, which match [Error Names](https://states-language.net/spec.html#error-names).

When a state reports an error, the interpreter scans through the Retriers and, when the Error Name appears in the value of a Retrier’s "ErrorEquals" field, implements the retry policy described in that Retrier.

An individual Retrier represents a certain number of retries, usually at increasing time intervals.

A Retrier MAY contain a field named "IntervalSeconds", whose value MUST be a positive integer, representing the number of seconds before the first retry attempt (default value: 1); a field named "MaxAttempts" whose value MUST be a non-negative integer, representing the maximum number of retry attempts (default: 3); and a field named "BackoffRate", a number which is the multiplier that increases the retry interval on each attempt (default: 2.0). The value of BackoffRate MUST be greater than or equal to 1.0.

Note that a "MaxAttempts" field whose value is 0 is legal, specifying that some error or errors should never be retried.

Here is an example of a Retrier which will make 2 retry attempts after waits of 3 and 4.5 seconds:

    "Retry" : [
        {
          "ErrorEquals": [ "States.Timeout" ],
          "IntervalSeconds": 3,
          "MaxAttempts": 2,
          "BackoffRate": 1.5
        }
    ]

The reserved name "States.ALL" in a Retrier’s "ErrorEquals" field is a wildcard and matches any Error Name. Such a value MUST appear alone in the "ErrorEquals" array and MUST appear in the last Retrier in the "Retry" array.

Here is an example of a Retrier which will retry any error except for "States.Timeout", using the default retry parameters.

    "Retry" : [
        {
          "ErrorEquals": [ "States.Timeout" ],
          "MaxAttempts": 0
        },
        {
          "ErrorEquals": [ "States.ALL" ]
        }
    ]

If the error recurs more times than allowed for by the "MaxAttempts" field, retries cease and normal error handling resumes.

#### Complex retry scenarios

A Retrier’s parameters apply across all visits to that Retrier in the context of a single state execution. This is best illustrated by example; consider the following Task State:

    "X": {
      "Type": "Task",
      "Resource": "arn:aws:states:us-east-1:123456789012:task:X",
      "Next": "Y",
      "Retry": [
        {
          "ErrorEquals": [ "ErrorA", "ErrorB" ],
          "IntervalSeconds": 1,
          "BackoffRate": 2,
          "MaxAttempts": 2
        },
        {
          "ErrorEquals": [ "ErrorC" ],
          "IntervalSeconds": 5
        }
      ],
      "Catch": [
        {
          "ErrorEquals": [ "States.ALL" ],
          "Next": "Z"
        }
      ]
    }

Suppose that this task fails four successive times, throwing Error Names "ErrorA", "ErrorB", "ErrorC", and "ErrorB". The first two errors match the first retrier and cause waits of one and two seconds. The third error matches the second retrier and causes a wait of five seconds. The fourth error would match the first retrier but its "MaxAttempts" ceiling of two retries has already been reached, so that Retrier fails, and execution is redirected to the "Z" state via the "Catch" field.

Note that once the interpreter transitions to another state in any way, all the Retrier parameters reset.

#### Fallback states

Task States, Parallel States, and Map States MAY have a field named "Catch", whose value MUST be an array of objects, called Catchers.

Each Catcher MUST contain a field named "ErrorEquals", specified exactly as with the Retrier "ErrorEquals" field, and a field named "Next" whose value MUST be a string exactly matching a State Name.

When a state reports an error and either there is no Retrier, or retries have failed to resolve the error, the interpreter scans through the Catchers in array order, and when the [Error Name](https://states-language.net/spec.html#error-names) appears in the value of a Catcher’s "ErrorEquals" field, transitions the machine to the state named in the value of the "Next" field.

The reserved name "States.ALL" appearing in a Retrier’s "ErrorEquals" field is a wildcard and matches any Error Name. Such a value MUST appear alone in the "ErrorEquals" array and MUST appear in the last Catcher in the "Catch" array.

#### Error output

When a state reports an error and it matches a Catcher, causing a transfer to another state, the state’s result (and thus the input to the state identified in the Catcher’s "Next" field) is a JSON object, called the Error Output. The Error Output MUST have a string-valued field named "Error", containing the Error Name. It SHOULD have a string-valued field named "Cause", containing human-readable text about the error.

A Catcher MAY have an "ResultPath" field, which works exactly like [a state’s top-level "ResultPath"](https://states-language.net/spec.html#filters), and may be used to inject the Error Output into the state’s original input to create the input for the Catcher’s "Next" state. The default value, if the "ResultPath" field is not provided, is "$", meaning that the output consists entirely of the Error Output.

Here is an example of a Catcher that will transition to the state named "RecoveryState" when a Lambda function throws an unhandled Java Exception, and otherwise to the "EndMachine" state, which is presumably Terminal.

Also in this example, if the first Catcher matches the Error Name, the input to "RecoveryState" will be the original state input, with the Error Output as the value of the top-level "error-info" field. For any other error, the input to "EndMachine" will just be the Error Output.

    "Catch": [
      {
        "ErrorEquals": [ "java.lang.Exception" ],
        "ResultPath": "$.error-info",
        "Next": "RecoveryState"
      },
      {
        "ErrorEquals": [ "States.ALL" ],
        "Next": "EndMachine"
      }
    ]

Each Catcher can specifiy multiple errors to handle.

When a state has both "Retry" and "Catch" fields, the interpreter uses any appropriate Retriers first and only applies the a matching Catcher transition if the retry policy fails to resolve the error.

</div>

<div id="states">

## State Types

As a reminder, the state type is given by the value of the "Type" field, which MUST appear in every State object.

### Table of State Types and Fields

Many fields can appear in more than one state type. The table below summarizes which fields can appear in which states. It excludes fields that are specific to one state type.

<table cellpadding="5">

<tbody>

<tr>

<td class="blank"></td>

<th align="center" colspan="8" _msthash="878566" _msttexthash="78429">States</th>

</tr>

<tr align="center">

<td class="blank"></td>

<th _msthash="878761" _msttexthash="45097">Task</th>

<th _msthash="878891" _msttexthash="112333">Parallel</th>

<th _msthash="879021" _msttexthash="30199">Map</th>

<th _msthash="879151" _msttexthash="45773">Pass</th>

<th _msthash="879281" _msttexthash="45370">Wait</th>

<th _msthash="879411" _msttexthash="73463">Choice</th>

<th _msthash="879541" _msttexthash="91273">Succeed</th>

<th _msthash="879671" _msttexthash="42783">Fail</th>

</tr>

<tr align="center">

<td align="right" class="field" _msthash="878540" _msttexthash="46462">Type</td>

<td align="center" class="required" _msthash="878670" _msttexthash="114465">Required</td>

<td align="center" class="required" _msthash="878800" _msttexthash="114465">Required</td>

<td align="center" class="required" _msthash="878930" _msttexthash="114465">Required</td>

<td align="center" class="required" _msthash="879060" _msttexthash="114465">Required</td>

<td align="center" class="required" _msthash="879190" _msttexthash="114465">Required</td>

<td align="center" class="required" _msthash="879320" _msttexthash="114465">Required</td>

<td align="center" class="required" _msthash="879450" _msttexthash="114465">Required</td>

<td align="center" class="required" _msthash="879580" _msttexthash="114465">Required</td>

</tr>

<tr align="center">

<td align="right" class="field" _msthash="878735" _msttexthash="95771">Comment</td>

<td align="center" class="allowed" _msthash="878865" _msttexthash="93886">Allowed</td>

<td align="center" class="allowed" _msthash="878995" _msttexthash="93886">Allowed</td>

<td align="center" class="allowed" _msthash="879125" _msttexthash="93886">Allowed</td>

<td align="center" class="allowed" _msthash="879255" _msttexthash="93886">Allowed</td>

<td align="center" class="allowed" _msthash="879385" _msttexthash="93886">Allowed</td>

<td align="center" class="allowed" _msthash="879515" _msttexthash="93886">Allowed</td>

<td align="center" class="allowed" _msthash="879645" _msttexthash="93886">Allowed</td>

<td align="center" class="allowed" _msthash="879775" _msttexthash="93886">Allowed</td>

</tr>

<tr align="center">

<td align="right" class="field" _msthash="878931" _msttexthash="437164">InputPath, OutputPath</td>

<td align="center" class="allowed" _msthash="879061" _msttexthash="93886">Allowed</td>

<td align="center" class="allowed" _msthash="879191" _msttexthash="93886">Allowed</td>

<td align="center" class="allowed" _msthash="879321" _msttexthash="93886">Allowed</td>

<td align="center" class="allowed" _msthash="879451" _msttexthash="93886">Allowed</td>

<td align="center" class="allowed" _msthash="879581" _msttexthash="93886">Allowed</td>

<td align="center" class="allowed" _msthash="879710" _msttexthash="93886">Allowed</td>

<td align="center" class="allowed" _msthash="879840" _msttexthash="93886">Allowed</td>

<td align="center" class="empty"></td>

</tr>

<tr align="center">

<td align="right" class="field" _msthash="879126" _msttexthash="466102">_One of:_ Next _or_ "End":true</td>

<td align="center" class="required" _msthash="879256" _msttexthash="114465">Required</td>

<td align="center" class="required" _msthash="879386" _msttexthash="114465">Required</td>

<td align="center" class="required" _msthash="879516" _msttexthash="114465">Required</td>

<td align="center" class="required" _msthash="879646" _msttexthash="114465">Required</td>

<td align="center" class="required" _msthash="879776" _msttexthash="114465">Required</td>

<td align="center" class="empty"></td>

<td align="center" class="empty"></td>

<td align="center" class="empty"></td>

</tr>

<tr align="center">

<td align="right" class="field" _msthash="879322" _msttexthash="155597">ResultPath</td>

<td align="center" class="allowed" _msthash="879452" _msttexthash="93886">Allowed</td>

<td align="center" class="allowed" _msthash="879582" _msttexthash="93886">Allowed</td>

<td align="center" class="allowed" _msthash="879711" _msttexthash="93886">Allowed</td>

<td align="center" class="allowed" _msthash="879841" _msttexthash="93886">Allowed</td>

<td align="center" class="empty"></td>

<td align="center" class="empty"></td>

<td align="center" class="empty"></td>

<td align="center" class="empty"></td>

</tr>

<tr align="center">

<td align="right" class="field" _msthash="879517" _msttexthash="158795">Parameters</td>

<td align="center" class="allowed" _msthash="879647" _msttexthash="93886">Allowed</td>

<td align="center" class="allowed" _msthash="879777" _msttexthash="93886">Allowed</td>

<td align="center" class="allowed" _msthash="879905" _msttexthash="93886">Allowed</td>

<td align="center" class="allowed" _msthash="880035" _msttexthash="93886">Allowed</td>

<td align="center" class="empty"></td>

<td align="center" class="empty"></td>

<td align="center" class="empty"></td>

<td align="center" class="empty"></td>

</tr>

<tr align="center">

<td align="right" class="field" _msthash="879712" _msttexthash="260728">ResultSelector</td>

<td align="center" class="allowed" _msthash="879842" _msttexthash="93886">Allowed</td>

<td align="center" class="allowed" _msthash="879970" _msttexthash="93886">Allowed</td>

<td align="center" class="allowed" _msthash="880100" _msttexthash="93886">Allowed</td>

<td align="center" class="empty"></td>

<td align="center" class="empty"></td>

<td align="center" class="empty"></td>

<td align="center" class="empty"></td>

<td align="center" class="empty"></td>

</tr>

<tr align="center">

<td align="right" class="field" _msthash="879906" _msttexthash="165698">Retry, Catch</td>

<td align="center" class="allowed" _msthash="880036" _msttexthash="93886">Allowed</td>

<td align="center" class="allowed" _msthash="880165" _msttexthash="93886">Allowed</td>

<td align="center" class="allowed" _msthash="880295" _msttexthash="93886">Allowed</td>

<td align="center" class="empty"></td>

<td align="center" class="empty"></td>

<td align="center" class="empty"></td>

<td align="center" class="empty"></td>

<td align="center" class="empty"></td>

</tr>

</tbody>

</table>

### Pass State

<font _mstmutation="1" _msthash="149318" _msttexthash="4891302">The Pass State (identified by ) by default passes its input to its output, performing no work.</font>`"Type":"Pass"`

A Pass State MAY have a field named "Result". If present, its value is treated as the output of a virtual task, and placed as prescribed by the "ResultPath" field, if any, to be passed on to the next state. If "Result" is not provided, the output is the input. Thus if neither "Result" nor "ResultPath" are provided, the Pass State copies its input through to its output.

Here is an example of a Pass State that injects some fixed data into the state machine, probably for testing purposes.

    "No-op": {
      "Type": "Pass",
      "Result": {
        "x-datum": 0.381018,
        "y-datum": 622.2269926397355
      },
      "ResultPath": "$.coords",
      "Next": "End"
    }

Suppose the input to this state were as follows:

    {
      "georefOf": "Home"
    }

Then the output would be:

    {
      "georefOf": "Home",
      "coords": {
        "x-datum": 0.381018,
        "y-datum": 622.2269926397355
      }
    }

### Task State

<font _mstmutation="1" _msthash="165451" _msttexthash="16924141">The Task State (identified by ) causes the interpreter to execute the work identified by the state’s "Resource" field.</font>`"Type":"Task"`

Here is an example:

    "TaskState": {
      "Comment": "Task State example",
      "Type": "Task",
      "Resource": "arn:aws:states:us-east-1:123456789012:task:HelloWorld",
      "Next": "NextState",
      "TimeoutSeconds": 300,
      "HeartbeatSeconds": 60
    }

A Task State MUST include a "Resource" field, whose value MUST be a URI that uniquely identifies the specific task to execute. The States language does not constrain the URI scheme nor any other part of the URI.

A Task State MAY include a "Parameters" field, whose value MUST be a Payload Template. A Task State MAY include a "ResultSelector" field, whose value MUST be a Payload Template.

Tasks can optionally specify timeouts. Timeouts (the "TimeoutSeconds" and "HeartbeatSeconds" fields) are specified in seconds and MUST be positive integers.

Both the total and heartbeat timeouts can be provided indirectly. A Task State may have "TimeoutSecondsPath" and "HeartbeatSecondsPath" fields which MUST be Reference Paths which, when resolved, MUST select fields whose values are positive integers. A Task State MUST NOT include both "TimeoutSeconds" and "TimeoutSecondsPath" or both "HeartbeatSeconds" and "HeartbeatSecondsPath".

If provided, the "HeartbeatSeconds" interval MUST be smaller than the "TimeoutSeconds" value.

If not provided, the default value of "TimeoutSeconds" is 60.

<font _mstmutation="1" _msthash="165438" _msttexthash="19605833">If the state runs longer than the specified timeout, or if more time than the specified heartbeat elapses between heartbeats from the task, then the interpreter fails the state with a Error Name.</font>`States.Timeout`

### Choice State

<font _mstmutation="1" _msthash="165698" _msttexthash="2893982">A Choice State (identified by ) adds branching logic to a state machine.</font> `"Type":"Choice"`

A Choice State MUST have a "Choices" field whose value is a non-empty array. Each element of the array MUST be a JSON object and is called a Choice Rule. A Choice Rule may be evaluated to return a boolean value. A Choice Rule at the top level, i.e. which is a member of the "Choices" array, MUST have a "Next" field, whose value MUST match a state name.

The interpreter attempts pattern-matches against the top-level Choice Rules in array order and transitions to the state specified in the "Next" field on the first Choice Rule where there is an exact match between the input value and a member of the comparison-operator array.

Here is an example of a Choice State.

    "DispatchEvent": {
      "Type" : "Choice",
      "Choices": [
        {
            "Not": {
              "Variable": "$.type",
              "StringEquals": "Private"
            },
            "Next": "Public"
        },
        {
          "And": [
    	{
    	  "Variable": "$.value",
    	  "IsPresent": true
    	},
    	{
              "Variable": "$.value",
              "IsNumeric": true
            },
            {
              "Variable": "$.value",
              "NumericGreaterThanEquals": 20
            },
            {
              "Variable": "$.value",
              "NumericLessThan": 30
            }
          ],
          "Next": "ValueInTwenties"
        },
        {
          "Variable": "$.rating",
          "NumericGreaterThanPath": "$.auditThreshold",
          "Next": "StartAudit"
        }
      ],
      "Default": "RecordEvent"
    }

In this example, suppose the machine is started with an input value of:

    {
      "type": "Private",
      "value": 22
    }

Then the interpreter will transition to the "ValueInTwenties" state, based on the "value" field.

A Choice Rule MUST be either a Boolean Expression or a Data-test Expression.

#### Boolean expression

A Boolean Expression is a JSON object which contains a field named "And", "Or", or "Not". If the field name is "And" or "Or", the value MUST be an non-empty object array of Choice Rules, which MUST NOT contain "Next" fields; the interpreter processes the array elements in order, performing the boolean evaluations in the expected fashion, ceasing array processing when the boolean value has been unambiguously determined.

The value of a Boolean Expression containing a "Not" field MUST be a single Choice Rule, that MUST NOT contain a "Next" field; it returns the inverse of the boolean to which the Choice Rule evaluates.

#### Data-test expression

A Data-test Expression Choice Rule is an assertion about a field and its value which yields a boolean depending on the data. A Data-test Expression MUST contain a field named "Variable" whose value MUST be a Path.

Each choice rule MUST contain exactly one field containing a comparison operator. The following comparison operators are supported:

1.  StringEquals, StringEqualsPath

2.  StringLessThan, StringLessThanPath

3.  StringGreaterThan, StringGreaterThanPath

4.  StringLessThanEquals, StringLessThanEqualsPath

5.  StringGreaterThanEquals, StringGreaterThanEqualsPath

6.  StringMatches

    <font _mstmutation="1" _msthash="420160" _msttexthash="54046668">Note: The value MUST be a String which MAY contain one or more "*" characters. The expression yields true if the data value selected by the Variable Path matches the value, where "*" in the value matches zero or more characters. Thus, matches , matches , and matches . No characters other than "*" have any special meaning during matching.</font>`foo*.log``foo23.log``*.log``zebra.log``foo*.*``foobar.zebra`

    If the character "*" needs to appear as part of the value without serving as a wildcard, it MUST be escaped with a backslash.

    If the character "\" needs to appear as part of the value without serving as an escape character, it MUST be escaped with a backslash.

    <font _mstmutation="1" _msthash="420511" _msttexthash="2473484">The literal string represents .  
    The literal string represents .</font> `\*``*``\\``\`

    In JSON, all backslashes contained in a string literal value must be escaped with another backslash, therefore, the above will equate to:

    <font _mstmutation="1" _msthash="420745" _msttexthash="2456948">The escaped string represents .  
    The escaped string represents .</font> `\\*``*``\\\\``\`

    <font _mstmutation="1" _msthash="420862" _msttexthash="6671990">If an open escape backslash is found in the StringMatches string, the interpreter will throw a runtime error.</font> `\`

7.  NumericEquals, NumericEqualsPath

8.  NumericLessThan, NumericLessThanPath

9.  NumericGreaterThan, NumericGreaterThanPath

10.  NumericLessThanEquals, NumericLessThanEqualsPath

11.  NumericGreaterThanEquals, NumericGreaterThanEqualsPath

12.  BooleanEquals, BooleanEqualsPath

13.  TimestampEquals, TimestampEqualsPath

14.  TimestampLessThan, TimestampLessThanPath

15.  TimestampGreaterThan, TimestampGreaterThanPath

16.  TimestampLessThanEquals, TimestampLessThanEqualsPath

17.  TimestampGreaterThanEquals, TimestampGreaterThanEqualsPath

18.  IsNull

    <font _mstmutation="1" _msthash="445978" _msttexthash="1819857">Note: This means the value is the built-in JSON literal .</font>`null`

19.  IsPresent

    Note: In this case, if the Variable-field Path fails to match anything in the input no exception is thrown and the Choice Rule just returns false.

20.  IsNumeric

21.  IsString

22.  IsBoolean

23.  IsTimestamp

For those operators that end with "Path", the value MUST be a Path, to be applied to the state’s effective input to yield a value to be compared with the value yielded by the Variable path.

For each operator which compares values, if the values are not both of the appropriate type (String, number, boolean, or [Timestamp](https://states-language.net/spec.html#timestamps)) the comparison will return false. Note that a field which is thought of as a timestamp could be matched by a string-typed comparator.

The various String comparators compare strings character-by-character with no special treatments such as case-folding, white-space collapsing, or [Unicode form normalization](https://unicode.org/reports/tr15/).

Note that for interoperability, numeric comparisons should not be assumed to work with values outside the magnitude or precision representable using the IEEE 754-2008 "binary64" data type. In particular, integers outside of the range [-(2<sup>53</sup>)+1, (2<sup>53</sup>)-1] might fail to compare in the expected way.

A Choice State MAY have a "Default" field, whose value MUST be a string whose value MUST match a State name; that state will execute if none of the Choice Rules match. The interpreter will raise a runtime States.NoChoiceMatched error if a Choice State fails to match a Choice Rule and no "Default" transition was specified.

A Choice State MUST NOT be an End state.

### Wait State

<font _mstmutation="1" _msthash="165139" _msttexthash="36652369">A Wait State (identified by ) causes the interpreter to delay the machine from continuing for a specified time. The time can be specified as a wait duration, specified in seconds, or an absolute expiry time, specified as an ISO-8601 extended offset date-time format string.</font>`"Type":"Wait"`

For example, the following Wait State introduces a ten-second delay into a state machine:

    "wait_ten_seconds" : {
      "Type" : "Wait",
      "Seconds" : 10,
      "Next": "NextState"
    }

This waits until an absolute time:

    "wait_until" : {
      "Type": "Wait",
      "Timestamp": "2016-03-14T01:59:00Z",
      "Next": "NextState"
    }

<font _mstmutation="1" _msthash="165789" _msttexthash="14712750">The wait duration does not need to be hardcoded. Here is the same example, reworked to look up the timestamp time using a Reference Path to the data, which might look like :</font>`{ "expirydate": "2016-03-14T01:59:00Z" }`

    "wait_until" : {
        "Type": "Wait",
        "TimestampPath": "$.expirydate",
        "Next": "NextState"
    }

A Wait State MUST contain exactly one of "Seconds", "SecondsPath", "Timestamp", or "TimestampPath".

### Succeed State

<font _mstmutation="1" _msthash="166309" _msttexthash="33661784">The Succeed State (identified by ) either terminates a state machine successfully, ends a branch of a Parallel State, or ends an iteration of a Map State. The output of a Succeed State is the same as its input, possibly modified by "InputPath" and/or "OutputPath".</font>`"Type":"Succeed"`

The Succeed State is a useful target for Choice-State branches that don't do anything except terminate the machine.

Here is an example:

    "SuccessState": {
      "Type": "Succeed"
    }

Because Succeed States are terminal states, they have no "Next" field.

### Fail State

<font _mstmutation="1" _msthash="165906" _msttexthash="3584997">The Fail State (identified by ) terminates the machine and marks it as a failure.</font> `"Type":"Fail"`

Here is an example:

    "FailState": {
              "Type": "Fail",
              "Error": "ErrorA",
              "Cause": "Kaiju attack"
    }

A Fail State MUST have a string field named "Error", used to provide an error name that can be used for error handling (Retry/Catch), operational, or diagnostic purposes. A Fail State MUST have a string field named "Cause", used to provide a human-readable message.

Because Fail States are terminal states, they have no "Next" field.

### Parallel State

<font _mstmutation="1" _msthash="165503" _msttexthash="3361813">The Parallel State (identified by ) causes parallel execution of "branches".</font>`"Type":"Parallel"`

Here is an example:

    "LookupCustomerInfo": {
      "Type": "Parallel",
      "Branches": [
        {
          "StartAt": "LookupAddress",
          "States": {
            "LookupAddress": {
              "Type": "Task",
              "Resource":
                "arn:aws:lambda:us-east-1:123456789012:function:AddressFinder",
              "End": true
            }
          }
        },
        {
          "StartAt": "LookupPhone",
          "States": {
            "LookupPhone": {
              "Type": "Task",
              "Resource":
                "arn:aws:lambda:us-east-1:123456789012:function:PhoneFinder",
              "End": true
            }
          }
        }
      ],
      "Next": "NextState"
    }

A Parallel State causes the interpreter to execute each branch starting with the state named in its "StartAt" field, as concurrently as possible, and wait until each branch terminates (reaches a terminal state) before processing the Parallel State's "Next" field. In the above example, this means the interpreter waits for "LookupAddress" and "LookupPhoneNumber" to both finish before transitioning to "NextState".

In the example above, the LookupAddress and LookupPhoneNumber branches are executed in parallel.

A Parallel State MUST contain a field named "Branches" which is an array whose elements MUST be objects. Each object MUST contain fields named "States" and "StartAt" whose meanings are exactly like those in the top level of a State Machine.

A state in a Parallel State branch "States" field MUST NOT have a "Next" field that targets a field outside of that "States" field. A state MUST NOT have a "Next" field which matches a state name inside a Parallel State branch’s "States" field unless it is also inside the same "States" field.

Put another way, states in a branch’s "States" field can transition only to each other, and no state outside of that "States" field can transition into it.

If any branch fails, due to an unhandled error or by transitioning to a Fail State, the entire Parallel State is considered to have failed and all the branches are terminated. If the error is not handled by the Parallel State, the interpreter should terminate the machine execution with an error.

Unlike a Fail State, a Succeed State within a Parallel merely terminates its own branch. A Succeed State passes its input through as its output, possibly modified by "InputPath" and "OutputPath".

The Parallel State passes its input (potentially as filtered by the "InputPath" field) as the input to each branch’s "StartAt" state. It generates a result which is an array with one element for each branch containing the output from that branch. The elements of the output array correspond to the branches in the same order that they appear in the "Branches" array. There is no requirement that all elements be of the same type.

The output array can be inserted into the input data using the state’s "ResultPath" field in the usual way.

For example, consider the following Parallel State:

    "FunWithMath": {
      "Type": "Parallel",
      "Branches": [
        {
          "StartAt": "Add",
          "States": {
            "Add": {
              "Type": "Task",
              "Resource": "arn:aws:states:::task:Add",
              "End": true
            }
          }
        },
        {
          "StartAt": "Subtract",
          "States": {
            "Subtract": {
              "Type": "Task",
              "Resource": "arn:aws:states:::task:Subtract",
              "End": true
            }
          }
        }
      ],
      "Next": "NextState"
    }

<font _mstmutation="1" _msthash="166140" _msttexthash="30945356">If the "FunWithMath" state was given the JSON array as input, then both the "Add" and "Subtract" states would receive that array as input. The output of "Add" would be , that of "Subtract" would be , and the output of the Parallel State would be a JSON array:</font>`[3, 2]``5``1`

    [ 5, 1 ]

### Map State

<font _mstmutation="1" _msthash="166530" _msttexthash="35207120">The Map State (identified by ) causes the interpreter to process all the elements of an array, potentially in parallel, with the processing of each element independent of the others. This document uses the term "iteration" to describe each such nested execution.</font>`"Type": "Map"`

The Parallel State applies multiple different state-machine branches to the same input, while the Map State applies a single state machine to multiple input elements.

There are several fields which may be used to control the execution. To summarize:

1.  The "Iterator" field’s value is an object that defines a state machine which will process each element of the array.

2.  The "ItemsPath" field’s value is a Reference Path identifying where in the effective input the array field is found.

3.  The "MaxConcurrency" field’s value is an integer that provides an upper bound on how many invocations of the Iterator may run in parallel.

Consider the following example input data:

    {
      "ship-date": "2016-03-14T01:59:00Z",
      "detail": {
        "delivery-partner": "UQS",
        "shipped": [
          { "prod": "R31", "dest-code": 9511, "quantity": 1344 },
          { "prod": "S39", "dest-code": 9511, "quantity": 40 },
          { "prod": "R31", "dest-code": 9833, "quantity": 12 },
          { "prod": "R40", "dest-code": 9860, "quantity": 887 },
          { "prod": "R40", "dest-code": 9511, "quantity": 1220 }
        ]
      }
    }

Suppose it is desired to apply a single Lambda function, "ship-val", to each of the elements of the "shipped" array. Here is an example of an appropriate Map State.

    "Validate-All": {
      "Type": "Map",
      "InputPath": "$.detail",
      "ItemsPath": "$.shipped",
      "MaxConcurrency": 0,
      "Iterator": {
        "StartAt": "Validate",
        "States": {
          "Validate": {
            "Type": "Task",
            "Resource": "arn:aws:lambda:us-east-1:123456789012:function:ship-val",
            "End": true
          }
        }
      },
      "ResultPath": "$.detail.shipped",
      "End": true
    }

In the example above, the "ship-val" Lambda function will be executed once for each element of the "shipped" field. The input to one iteration will be:

    {
      "prod": "R31",
      "dest-code": 9511,
      "quantity": 1344
    }

Suppose that the "ship-val" function also needs access to the shipment’s courier, which would be the same in each iteration. The ["Parameters"](https://states-language.net/spec.html#parameters) field may be used to construct the raw input for each iteration:

    "Validate-All": {
      "Type": "Map",
      "InputPath": "$.detail",
      "ItemsPath": "$.shipped",
      "MaxConcurrency": 0,
      "Parameters": {
        "parcel.$": "$.Map.Item.Value",
        "courier.$": "$.delivery-partner"
      },
      "Iterator": {
        "StartAt": "Validate",
        "States": {
          "Validate": {
            "Type": "Task",
            "Resource": "arn:aws:lambda:us-east-1:123456789012:function:ship-val",
            "End": true
          }
        }
      },
      "ResultPath": "$.detail.shipped",
      "End": true
    }

The "ship-val" Lambda function will be executed once for each element of the array selected by "ItemsPath". In the example above, the raw input to one iteration, as specified by "Parameters", will be:

    {
      "parcel": {
        "prod": "R31",
        "dest-code": 9511,
        "quantity": 1344
       },
       "courier": "UQS"
    }

In the examples above, the ResultPath results in the output being the same as the input, with the "detail.shipped" field being overwritten by an array in which each element is the output of the "ship-val" Lambda function as applied to the corresponding input element.

#### Map State input/output processing

The "InputPath" field operates as usual, selecting part of the raw input - in the example, the value of the "detail" field - to serve as the effective input.

A Map State MAY have a "ItemsPath" field, whose value MUST be a Reference Path. The Reference Path is applied to the effective input and MUST identify a field whose value is a JSON array.

The default value of "ItemsPath" is "$", which is to say the whole effective input. So, if a Map State has neither an "InputPath" nor a "ItemsPath" field, it is assuming that the raw input to the state will be a JSON array.

The input to each invocation, by default, is a single element of the array field identified by the "ItemsPath" value, but may be overridden using the ["Parameters"](https://states-language.net/spec.html#parameters) field.

In each iteration, within the Map State (but not child states within an Iterator field), the Context Object will have an object field named "Map" which contains an object field named "Item" which in turn contains an integer field named "Index" whose value is the (zero-based) array index being processed in the iteration and a field named "Value", whose value is the array element being processed.

A Map State’s result is an array containing one element for each element of the ItemsPath input array, in the same order.

#### Map State concurrency

A Map State MAY have a non-negative integer "MaxConcurrency" field. Its default value is zero, which places no limit on invocation parallelism and requests the interpreter to execute the iterations as concurrently as possible.

If "MaxConcurrency" has a non-zero value, the interpreter will not allow the number of concurrent iterations to exceed that value.

A MaxConcurrency value of 1 is special, having the effect that interpreter will invoke the Iterator once for each array element in the order of their appearance in the input, and will not start an iteration until the previous iteration has completed execution.

#### Map State Iterator definition

A Map State MUST contain an object field named "Iterator" which MUST contain fields named "States" and "StartAt", whose meanings are exactly like those in the top level of a State Machine.

A state in the "States" field of an "Iterator" field MUST NOT have a "Next" field that targets a field outside of that "States" field. A state MUST NOT have a "Next" field which matches a state name inside an "Iterator" field’s "States" field unless it is also inside the same "States" field.

Put another way, states in an Iterator’s "States" field can transition only to each other, and no state outside of that "States" field can transition into it.

If any iteration fails, due to an unhandled error or by transitioning to a Fail state, the entire Map State is considered to have failed and all the iterations are terminated. If the error is not handled by the Map State, the interpreter should terminate the machine execution with an error.

Unlike a Fail State, a Succeed State within a Map merely terminates its own iteration. A Succeed State passes its input through as its output, possibly modified by "InputPath" and "OutputPath".

</div>

<div id="appendices">

## Appendices

### Appendix A: Predefined Error Codes

<table cellpadding="5">

<tbody>

<tr>

<th _msthash="1086332" _msttexthash="42471">Code</th>

<th _msthash="1086462" _msttexthash="183612">Description</th>

</tr>

<tr>

<td _msthash="1086111" _msttexthash="128661">States.ALL</td>

<td>

A wildcard which matches any Error Name.

</td>

</tr>

<tr>

<td _msthash="1086306" _msttexthash="554359">States.HeartbeatTimeout</td>

<td>

A Task State failed to heartbeat for a time longer than the "HeartbeatSeconds" value.

</td>

</tr>

<tr>

<td _msthash="1086501" _msttexthash="251992">States.Timeout</td>

<td>

A Task State either ran longer than the "TimeoutSeconds" value, or failed to heartbeat for a time longer than the "HeartbeatSeconds" value.

</td>

</tr>

<tr>

<td _msthash="1086696" _msttexthash="323882">States.TaskFailed</td>

<td>

A Task State failed during the execution.

</td>

</tr>

<tr>

<td _msthash="1086891" _msttexthash="380315">States.Permissions</td>

<td>

A Task State failed because it had insufficient privileges to execute the specified code.

</td>

</tr>

<tr>

<td _msthash="1087086" _msttexthash="801437">States.ResultPathMatchFailure</td>

<td>

A state’s "ResultPath" field cannot be applied to the input the state received.

</td>

</tr>

<tr>

<td _msthash="1087281" _msttexthash="712140">States.ParameterPathFailure</td>

<td>

Within a state’s "Parameters" field, the attempt to replace a field whose name ends in ".$" using a Path failed.

</td>

</tr>

<tr>

<td _msthash="1087476" _msttexthash="384800">States.BranchFailed</td>

<td>

A branch of a Parallel State failed.

</td>

</tr>

<tr>

<td _msthash="1087671" _msttexthash="490581">States.NoChoiceMatched</td>

<td>

A Choice State failed to find a match for the condition field extracted from its input.

</td>

</tr>

<tr>

<td _msthash="1129804" _msttexthash="551343">States.IntrinsicFailure</td>

<td>

Within a Payload Template, the attempt to invoke an Intrinsic Function failed.

</td>

</tr>

</tbody>

</table>

### Appendix B: List of Intrinsic Functions

#### States.Format

<font _mstmutation="1" _msthash="245661" _msttexthash="85367230">This Intrinsic Function takes one or more arguments. The Value of the first MUST be a string, which MAY include zero or more instances of the character sequence . There MUST be as many remaining arguments in the Intrinsic Function as there are occurrences of . The interpreter returns the first-argument string with each replaced by the Value of the positionally-corresponding argument in the Intrinsic Function.</font>`{}``{}``{}`

<font _mstmutation="1" _msthash="245778" _msttexthash="2768116">If necessary, the and characters can be escaped respectively as and .</font>`{``}``\\{``\\}`

<font _mstmutation="1" _msthash="245895" _msttexthash="36606037">If the argument is a Path, applying it to the input MUST yield a value that is a string, a boolean, a number, or . In each case, the Value is the natural string representation; string values are not accompanied by enclosing characters. The Value MUST NOT be a JSON array or object.</font>`null``"`

For example, given the following Payload Template:

    {
      "Parameters": {
        "foo.$": "States.Format('Your name is {}, we are in the year {}', $.name, 2020)"
      }
    }

Suppose the input to the Payload Template is as follows:

    {
      "name": "Foo",
      "zebra": "stripe"
    }

After processing the Payload Template, the new payload becomes:

    {
      "foo": "Your name is Foo, we are in the year 2020"
    }

#### States.StringToJson

This Intrinsic Function takes a single argument whose Value MUST be a string. The interpreter applies a JSON parser to the Value and returns its parsed JSON form.

For example, given the following Payload Template:

    {
      "Parameters": {
        "foo.$": "States.StringToJson($.someString)"
      }
    }

Suppose the input to the Payload Template is as follows:

    {
      "someString": "{\"number\": 20}",
      "zebra": "stripe"
    }

After processing the Payload Template, the new payload becomes:

    {
      "foo": {
        "number": 20
      }
    }

#### States.JsonToString

This Intrinsic Function takes a single argument which MUST be a Path. The interpreter returns a string which is a JSON text representing the data identified by the Path.

For example, given the following Payload Template:

    {
      "Parameters": {
        "foo.$": "States.JsonToString($.someJson)"
      }
    }

Suppose the input to the Payload Template is as follows:

    {
      "someJson": {
        "name": "Foo",
        "year": 2020
      },
      "zebra": "stripe"
    }

After processing the Payload Template, the new payload becomes:

    {
      "foo": "{\"name\":\"Foo\",\"year\":2020}"
    }

#### States.Array

This Intrinsic Function takes zero or more arguments. The interpreter returns a JSON array containing the Values of the arguments, in the order provided.

For example, given the following Payload Template:

    {
      "Parameters": {
        "foo.$": "States.Array('Foo', 2020, $.someJson, null)"
      }
    }

Suppose the input to the Payload Template is as follows:

    {
      "someJson": {
        "random": "abcdefg"
      },
      "zebra": "stripe"
    }

After processing the Payload Template, the new payload becomes:

    {
      "foo": [
        "Foo",
        2020,
        {
          "random": "abcdefg"
        },
        null
      ]
    }

</div>

<div id="document-history">

## Document History

### August 11, 2020

*   Choice Rules added

*   StringMatches

*   IsNull, IsPresent, IsNumeric, IsString, IsBoolean, IsTimestamp

*   StringEqualsPath, StringLessThanPath, StringGreaterThanPath, StringLessThanEqualsPath, StringGreaterThanEqualsPath, NumericEqualsPath, NumericLessThanPath, NumericGreaterThanPath, NumericLessThanEqualsPath, NumericGreaterThanEqualsPath, BooleanEqualsPath, TimestampEqualsPath, TimestampLessThanPath, TimestampGreaterThanPath, TimestampLessThanEqualsPath, TimestampGreaterThanEqualsPath

*   TimeoutSecondsPath and HeartbeatSecondsPath added to Task State

*   Payload Template added

*   ResultSelector in Task State, Parallel State, and Map State

*   Intrinsic Functions added

*   States.Format

*   States.StringToJson

*   States.JsonToString

*   States.Array

</div>
