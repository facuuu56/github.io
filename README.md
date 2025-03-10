import { useState } from 'react'
import { Button } from "/components/ui/button"
import { Card, CardContent, CardHeader, CardTitle } from "/components/ui/card"
import { Check, X } from "lucide-react"

type Question = {
  question: string
  options: string[]
  correctAnswer: string
}

export default function FacuQuiz() {
  const [currentQuestion, setCurrentQuestion] = useState(0)
  const [score, setScore] = useState(0)
  const [showExplanation, setShowExplanation] = useState(false)
  const [selectedAnswer, setSelectedAnswer] = useState<string | null>(null)

  const questions: Question[] = [
    {
      question: "¿Quién ganó la Copa Libertadores 2022?",
      options: ["Flamengo", "Fluminense", "Independiente", "Boca Juniors"],
      correctAnswer: "Flamengo",
    },
    {
      question: "¿Cuál es el equipo con más títulos de UEFA Champions League?",
      options: ["Real Madrid", "Bayern Munich", "AC Milan", "Liverpool"],
      correctAnswer: "Real Madrid",
    },
    {
      question: "¿En qué año Pelé marcó su primer gol para Santos?",
      options: ["1954", "1955", "1956", "1957"],
      correctAnswer: "1956",
    },
    {
      question: "¿Quién es el máximo goleador de la historia de la Copa del Mundo?",
      options: ["Miroslav Klose", "Cristiano Ronaldo", "Lionel Messi", "Diego Maradona"],
      correctAnswer: "Miroslav Klose",
    },
    {
      question: "¿Cuál es el equipo con más títulos de Copa América?",
      options: ["Argentina", "Brasil", "Uruguay", "Colombia"],
      correctAnswer: "Brasil",
    },
    {
      question: "¿Quién ganó la Copa del Mundo 2018?",
      options: ["Alemania", "Francia", "España", "Portugal"],
      correctAnswer: "Francia",
    },
    {
      question: "¿Cuál es el máximo goleador de la historia de la Copa Libertadores?",
      options: ["Lionel Messi", "Radamel Falcao", "Carlos Tevez", "Neymar"],
      correctAnswer: "Lionel Messi",
    },
    {
      question: "¿En qué año se celebró la primera Copa América?",
      options: ["1916", "1920", "1925", "1930"],
      correctAnswer: "1916",
    },
    {
      question: "¿Quién es el máximo goleador de la historia de la UEFA Champions League?",
      options: ["Cristiano Ronaldo", "Lionel Messi", "Robert Lewandowski", "Karim Benzema"],
      correctAnswer: "Cristiano Ronaldo",
    },
    {
      question: "¿Cuál es el equipo con más títulos de Copa del Mundo?",
      options: ["Alemania", "Brasil", "Italia", "Argentina"],
      correctAnswer: "Brasil",
    },
    {
      question: "¿Quién ganó la Copa América 2021?",
      options: ["Argentina", "Brasil", "Colombia", "Ecuador"],
      correctAnswer: "Argentina",
    },
    {
      question: "¿En qué año se celebró la primera UEFA Champions League?",
      options: ["1955", "1956", "1957", "1958"],
      correctAnswer: "1955",
    },
    {
      question: "¿Quién es el máximo goleador de la historia de la Copa América?",
      options: ["Pelé", "Lionel Messi", "Diego Maradona", "Carlos Valderrama"],
      correctAnswer: "Pelé",
    },
    {
      question: "¿Cuál es el equipo con más títulos de Copa Libertadores?",
      options: ["Flamengo", "Independiente", "River Plate", "Boca Juniors"],
      correctAnswer: "Flamengo",
    },
    {
      question: "¿Quién ganó la Copa del Mundo 2014?",
      options: ["Alemania", "Brasil", "España", "Italia"],
      correctAnswer: "Alemania",
    },
    {
      question: "¿Cuál es el máximo goleador de la historia de la Copa del Mundo?",
      options: ["Miroslav Klose", "Cristiano Ronaldo", "Lionel Messi", "Diego Maradona"],
      correctAnswer: "Miroslav Klose",
    },
    {
      question: "¿Quién ganó la UEFA Champions League 2022?",
      options: ["Real Madrid", "Liverpool", "Manchester City", "Bayern Munich"],
      correctAnswer: "Manchester City",
    },
    {
      question: "¿En qué año se celebró la primera Copa del Mundo?",
      options: ["1930", "1934", "1938", "1942"],
      correctAnswer: "1930",
    },
    {
      question: "¿Quién es el máximo goleador de la historia de la UEFA Champions League?",
      options: ["Cristiano Ronaldo", "Lionel Messi", "Robert Lewandowski", "Karim Benzema"],
      correctAnswer: "Cristiano Ronaldo",
    },
    {
      question: "¿Cuál es el equipo con más títulos de Copa América?",
      options: ["Argentina", "Brasil", "Uruguay", "Colombia"],
      correctAnswer: "Brasil",
    },
    {
      question: "¿Quién ganó la Copa del Mundo 2010?",
      options: ["España", "Holanda", "Alemania", "Italia"],
      correctAnswer: "España",
    },
    {
      question: "¿Cuál es el máximo goleador de la historia de la Copa América?",
      options: ["Pelé", "Lionel Messi", "Diego Maradona", "Carlos Valderrama"],
      correctAnswer: "Pelé",
    },
    {
      question: "¿Cuál es el equipo con más títulos de Copa Libertadores?",
      options: ["Flamengo", "Independiente", "River Plate", "Boca Juniors"],
      correctAnswer: "Flamengo",
    },
    {
      question: "¿Quién ganó la Copa del Mundo 2006?",
      options: ["Alemania", "Italia", "Francia", "España"],
      correctAnswer: "Italia",
    },
    {
      question: "¿Cuál es el máximo goleador de la historia de la Copa del Mundo?",
      options: ["Miroslav Klose", "Cristiano Ronaldo", "Lionel Messi", "Diego Maradona"],
      correctAnswer: "Miroslav Klose",
    },
    {
      question: "¿Quién ganó la UEFA Champions League 2021?",
      options: ["Manchester City", "Chelsea", "Real Madrid", "PSG"],
      correctAnswer: "Manchester City",
    },
    {
      question: "¿En qué año se celebró la primera Copa del Mundo?",
      options: ["1930", "1934", "1938", "1942"],
      correctAnswer: "1930",
    },
    {
      question: "¿Quién es el máximo goleador de la historia de la UEFA Champions League?",
      options: ["Cristiano Ronaldo", "Lionel Messi", "Robert Lewandowski", "Karim Benzema"],
      correctAnswer: "Cristiano Ronaldo",
    },
    {
      question: "¿Cuál es el equipo con más títulos de Copa América?",
      options: ["Argentina", "Brasil", "Uruguay", "Colombia"],
      correctAnswer: "Brasil",
    },
    {
      question: "¿Quién ganó la Copa del Mundo 2002?",
      options: ["Brasil", "Alemania", "Italia", "Corea del Sur"],
      correctAnswer: "Brasil",
    },
    {
      question: "¿Cuál es el máximo goleador de la historia de la Copa América?",
      options: ["Pelé", "Lionel Messi", "Diego Maradona", "Carlos Valderrama"],
      correctAnswer: "Pelé",
    },
    {
      question: "¿Cuál es el equipo con más títulos de Copa Libertadores?",
      options: ["Flamengo", "Independiente", "River Plate", "Boca Juniors"],
      correctAnswer: "Flamengo",
    },
    {
      question: "¿Quién ganó la Copa del Mundo 1998?",
      options: ["Francia", "Alemania", "Italia", "Brasil"],
      correctAnswer: "Francia",
    },
    {
      question: "¿Cuál es el máximo goleador de la historia de la Copa del Mundo?",
      options: ["Miroslav Klose", "Cristiano Ronaldo", "Lionel Messi", "Diego Maradona"],
      correctAnswer: "Miroslav Klose",
    },
    {
      question: "¿Quién ganó la UEFA Champions League 2020?",
      options: ["Bayern Munich", "PSG", "Liverpool", "Manchester City"],
      correctAnswer: "Bayern Munich",
    },
    {
      question: "¿En qué año se celebró la primera Copa del Mundo?",
      options: ["1930", "1934", "1938", "1942"],
      correctAnswer: "1930",
    },
    {
      question: "¿Quién es el máximo goleador de la historia de la UEFA Champions League?",
      options: ["Cristiano Ronaldo", "Lionel Messi", "Robert Lewandowski", "Karim Benzema"],
      correctAnswer: "Cristiano Ronaldo",
    },
    {
      question: "¿Cuál es el equipo con más títulos de Copa América?",
      options: ["Argentina", "Brasil", "Uruguay", "Colombia"],
      correctAnswer: "Brasil",
    },
    {
      question: "¿Quién ganó la Copa del Mundo 1994?",
      options: ["Brasil", "Alemania", "Italia", "Argentina"],
      correctAnswer: "Brasil",
    },
    {
      question: "¿Cuál es el máximo goleador de la historia de la Copa América?",
      options: ["Pelé", "Lionel Messi", "Diego Maradona", "Carlos Valderrama"],
      correctAnswer: "Pelé",
    },
    {
      question: "¿Cuál es el equipo con más títulos de Copa Libertadores?",
      options: ["Flamengo", "Independiente", "River Plate", "Boca Juniors"],
      correctAnswer: "Flamengo",
    },
    {
      question: "¿Quién ganó la Copa del Mundo 1990?",
      options: ["Alemania", "Italia", "Argentina", "Francia"],
      correctAnswer: "Alemania",
    },
    {
      question: "¿Cuál es el máximo goleador de la historia de la Copa del Mundo?",
      options: ["Miroslav Klose", "Cristiano Ronaldo", "Lionel Messi", "Diego Maradona"],
      correctAnswer: "Miroslav Klose",
    },
    {
      question: "¿Quién ganó la UEFA Champions League 2019?",
      options: ["Liverpool", "Manchester City", "Real Madrid", "Tottenham"],
      correctAnswer: "Liverpool",
    },
    {
      question: "¿En qué año se celebró la primera Copa del Mundo?",
      options: ["1930", "1934", "1938", "1942"],
      correctAnswer: "1930",
    },
    {
      question: "¿Quién es el máximo goleador de la historia de la UEFA Champions League?",
      options: ["Cristiano Ronaldo", "Lionel Messi", "Robert Lewandowski", "Karim Benzema"],
      correctAnswer: "Cristiano Ronaldo",
    },
    {
      question: "¿Cuál es el equipo con más títulos de Copa América?",
      options: ["Argentina", "Brasil", "Uruguay", "Colombia"],
      correctAnswer: "Brasil",
    },
    {
      question: "¿Quién ganó la Copa del Mundo 1986?",
      options: ["Argentina", "Alemania", "Italia", "Francia"],
      correctAnswer: "Argentina",
    },
    {
      question: "¿Cuál es el máximo goleador de la historia de la Copa América?",
      options: ["Pelé", "Lionel Messi", "Diego Maradona", "Carlos Valderrama"],
      correctAnswer: "Pelé",
    },
    {
      question: "¿Cuál es el equipo con más títulos de Copa Libertadores?",
      options: ["Flamengo", "Independiente", "River Plate", "Boca Juniors"],
      correctAnswer: "Flamengo",
    },
  ]

  const handleAnswer = (selectedOption: string) => {
    setSelectedAnswer(selectedOption)
    setShowExplanation(true)

    if (selectedOption === questions[currentQuestion].correctAnswer) {
      setScore(score + 1)
    }
  }

  const nextQuestion = () => {
    setSelectedAnswer(null)
    setShowExplanation(false)
    setCurrentQuestion(currentQuestion + 1)
  }

  const resetQuiz = () => {
    setCurrentQuestion(0)
    setScore(0)
    setShowExplanation(false)
    setSelectedAnswer(null)
  }

  if (currentQuestion >= questions.length) {
    return (
      <Card className="w-full max-w-2xl mx-auto mt-8">
        <CardHeader>
          <CardTitle className="text-2xl text-center">¡Facu Quiz Completado!</CardTitle>
        </CardHeader>
        <CardContent className="space-y-4">
          <p className="text-xl text-center">
            Tu puntaje final: {score} de {questions.length}
          </p>
          <div className="text-center">
            <Button onClick={resetQuiz}>Intentar de nuevo</Button>
          </div>
        </CardContent>
      </Card>
    )
  }

  return (
    <Card className="w-full max-w-2xl mx-auto mt-8">
      <CardHeader>
        <CardTitle className="text-2xl">Facu Quiz</CardTitle>
        <p className="text-gray-500">Pregunta {currentQuestion + 1} de {questions.length}</p>
        <p className="text-gray-500">Puntaje: {score}</p>
      </CardHeader>
      <CardContent className="space-y-4">
        <h2 className="text-xl font-semibold">{questions[currentQuestion].question}</h2>
        <div className="grid grid-cols-1 gap-3">
          {questions[currentQuestion].options.map((option) => (
            <Button
              key={option}
              onClick={() => handleAnswer(option)}
              variant={
                showExplanation
                  ? option === questions[currentQuestion].correctAnswer
                    ? 'default'
                    : option === selectedAnswer
                    ? 'destructive'
                    : 'outline'
                  : 'outline'
              }
              disabled={showExplanation}
              className="p-4 text-left"
            >
              {option}
            </Button>
          ))}
        </div>

        {showExplanation && (
          <div className="mt-4 p-4 rounded-lg bg-gray-100">
            <p className="font-semibold">
              {selectedAnswer === questions[currentQuestion].correctAnswer ? (
                <>
                  <Check className="inline-block mr-2" /> ¡Correcto!
                </>
              ) : (
                <>
                  <X className="inline-block mr-2" /> Incorrecto!
                </>
              )}
            </p>
            <Button onClick={nextQuestion} className="mt-4">
              Siguiente Pregunta
            </Button>
          </div>
        )}
      </CardContent>
    </Card>
  )
}
