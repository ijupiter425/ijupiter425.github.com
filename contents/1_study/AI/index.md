# AI

source: `{{ page.path }}`

<QueryList>
  <Query Id="0" Path="Security">
    <Select Path="Security">*[System[(EventID=4688)]] and
      *[EventData[Data[@Name='NewProcessName'] = 'C:\Program Files (x86)\Nox\bin\Nox.exe']]
</Select>
  </Query>
</QueryList>

[TensorFlow][https://www.tensorflow.org/]
